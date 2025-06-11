genrule(
  name = "target",
  srcs = glob(["**/*.cs"], exclude = ["**/obj/**", "**/bin/**", "2/1/Data/**"]),
  outs = ["log.txt"],
  cmd = "echo $(SRCS) > $@",
  visibility = ["//visibility:public"],
)
