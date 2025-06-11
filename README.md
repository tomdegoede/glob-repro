Repro of a Bazel globbing error when folders are removed under the glob with --watchfs active on a Windows machine.

To trigger the error execute the following in Powershell
```pwsh
git checkout master ; sleep 2 ; bazel build //src:target ; sleep 2 ; git checkout master~2; sleep 2 ; bazel build //src:target
```
In this small reproduction it occurs flaky on my local machine. In our large monorepo it occurs every time. The repro has more chance of occuring after a `bazel shutdown`. When the error is raised consequtive calls to `bazel build` raise the error again.

this introduces errors:
```
ERROR: Skipping '//src:target': no such package 'src': error globbing [**/*.cs] - [**/obj/**, **/bin/**, 2/1/Data/**] op=FILES: D:/dev/bug/src/2/2/7/1/2 (No such file or directory)
ERROR: no such package 'src': error globbing [**/*.cs] - [**/obj/**, **/bin/**, 2/1/Data/**] op=FILES: D:/dev/bug/src/2/2/7/1/2 (No such file or directory)  
```
