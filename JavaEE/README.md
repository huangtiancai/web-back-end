1.重命名后  右键->refactor ->rename 
  或者  右键->properties ->web --> web project settings 下的Context root
  项目下的.project 文件的name标签值一般在复制项目重命名后就会更改
2.全局搜索老的工程名，发现在项目的根目录的.setting文件夹下org.eclipse.wst.common.component文件中项目名字没有变化
  xml中原项目的名字更改为复制后的项目名称
  