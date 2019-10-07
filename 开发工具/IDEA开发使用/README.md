## 创建Spring Boot 项目
1.New Spring Initialzr Project
使用开发工具IDEA新建一个工程，功能菜单选项是File - New - Project，在New Project下选择Spring Initializr功能选项
> - 在右侧内容页，选择Project SDK，此处使用的是JDK1.8.0
> - Initalizr Service URL选择Default: https://start.spring.io 默认选项即可

然后选择下一步Next

2.Project Metadata(元数据) 设置项目坐标及项目名称
- Group 
- Artifact
下面Name 和package 自动补全
- Type:Maven 项目
- Language:java
- Packaging:jar
- Java Version:对于JDK选择8
> - 坐标Group ID是项目组织唯一的标识符，实际对应项目中的package包。
> - 坐标Artifact ID是项目的唯一的标识符，实际对应项目的project name名称，Artifact不可包含大写字母。

3.Dependencies 初始化依赖
- Developer Tools
- Web
- Template Engines
- Security
- SQL
- NoSQl

4.项目结构展示


5.pom.xml 项目依赖管理 
