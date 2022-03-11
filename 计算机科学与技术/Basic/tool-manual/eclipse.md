# 1. 【快捷键】
1. **快速修复**：`Ctrl + 1`
1. **删除当前行**：`Ctrl + D`
1. **快速运行项目**：`Ctrl + F11`
1. **定位在某行**：`Ctrl + L`
1. **查看类的继承关系树** ：`Ctrl + T`
    > * 默认自顶向下，再按一次会变成自底向上的显示结构
    > * 选中方法名，按 Ctrl + T，可查看到有这个同名方法的父类、子类、接口

1. **单行注释**：`Ctrl + /`
1. **直接换行**：`Shift + Enter`
1. **向上换行**：`Ctrl + shift + Enter`
1. **当前行和下面一行交互位置**：`Alt + ↓`
1. **当前行和上面一行交互位置**：`Alt + ↑`
1. **复制当前行到下一行**：`Alt + CTRL + ↓`
1. **复制当前行到上一行**：`Alt + CTRL + ↑`
1. **大写**：`Ctrl + Shift + X`
1. **小写**：`Ctrl + Shift + Y`
1. **格式化当前代码**：`Ctrl + Shift + F`
1. **重命名**：`Alt + Shift + R`
1. **缺少的Import语句被加入，多余的Import语句被删除**：`Ctrl + Shift + O`
1. **保存所有未保存的文件**：`Ctrl + Shift + S`
1. **显示当前选择资源的属性**：`Alt + Enter`
1. **代码助手: 自动显示提示信息**：`Alt + /`
1. **查看方法说明**：`F2`
1. **向前向后**：`Alt + ←、→`
1. **查看源代码**：`Ctrl + shift + T`
1. **捕获异常**：`Alt + shift + z`
1. **抽取方法**：`Alt + Shift + M`
1. **抽取局部变量**：`Alt + Shift + L`

    > * 类似先按 `ctrl + 2`，紧接着按 `L` 补全赋值号左边的内容


1. **查看所有快捷键**：`Ctrl + shift + L`
1. **调试**
    > * `F5`：刷新或进入方法中
    > * `F6`：单步执行
    > * `F7`：跳出方法
    > * `F8`：继续跳到下一个断点

1. **打开资源**：`Ctrl + Shift + R`
1. **快速 outline**：`Ctrl + O` => 列出当前类中的所有方法及属性
1. **快速转换编辑器**：`Ctrl + E`
1. **为每一行的行首添加内容**：`Alt + Shift + A`
1. **为每一行的末尾添加内容**
    > * `Ctrl + F` 弹出框中勾选 Regular expressions
    > * 输入 `^(.*)$` 替换为 `\1后面加添加的内容`

1. **查找某个方法被谁调用**：`Ctrl + Shift + G`
1. **快速显示源菜单**：`Alt + Shift + S`

# 2. 【设置项】
1. **工作空间设置**：`File 菜单 -> Switch Workspace`

1. **设置字符编码集**：`General -> Workspace -> Text file encoding`

1. **设置字体与颜色**：`General -> Appearance -> colors and Fonts -> Basic -> Aa Text Font`

1. **修改快捷键**：`General -> Keys`

1. **配置 JRE**：`Java -> Installed JREs`
    > * **选择JDK的根目录**：`「add...」 → 「Standard VM」 → [JRE home]`
    > * **查看支持的JDK版本**：`Java -> Compiler`

1. **编辑器**
    > * 可关联不同类型的文件到不同类型的编辑器
    > * 双击文件时会在工作台中打开相应的编辑器，如果没有相应的内部编辑器，则会打开外部编辑器
    > * 右键选择 `Open With` 或 `General -> Editors -> File Associations`

1. **代码补全之设置触发器**
    > * 默认点操作符会触发属性或方法提示
    > * 可以设置任意字符触发提示：`Java -> Editor -> Content Assist -> Auto activation triggers for Java`

1. **代码模板**
    1. `Java -> Code Style -> Code Templates`
        * e.g. `Comments -> Types -> Edit`

        ```
        /**
        * @author ${user}
        * @date ${date}    // ${date} 由单击 Insert Variable ... 插入
        * ${tags}
        */

        // 当在类或接口上输入文档注释时自动生成以上代码
        ```

    2. `Java -> Editor -> Templates`

        ```
        New -> 输入名称：如 test 和 描述内容，其中 Pattern 中例如输入：
            System.out.println("start");
            ${line_selection}${cursor}   // 可通过单击 Insert Variable... 插入
            System.out.println("end");

        运用模板
            选中 System.out.println("yiyiqiang");
            按 Alt + shift + Z 选择 test(代码模板名)，则结果为：
                System.out.println("start");
                System.out.println("yiyiqiang");
                System.out.println("end");
        ```

1. **本地历史记录**：`General -> Workspace -> Local History`
    * 历史记录保存的时间：默认7天
    * 每个文件的最大保存条目：默认50
    * 文件最大大小：默认1MB

    > 1. **找回删除的文件**：项目右击 => `Restore from Local History`
    > 1. **比较文件的不同版本**：文件或编辑区右击 => `Compare With -> Local History...`
    > 1. **替换文件到历史版本**：文件或编辑区右击 => `Replace With -> Local History...`

# 3. 【常用功能】
1. **Eclipse 自动编译**
    > * Eclipse 会自动执行 `javac` 进行编译，并且会对编译错误直接给出提示

1. **Java 项目的 src 目录 和 bin目录**
    > * src 目录用于存放源代码，bin 目录用于存放 Eclipse 自动编译生成的 class 文件
    > * 在 Eclipse 视图里可以看到 src 目录，而自动隐藏了 bin 目录

1. **导入导出项目**
    > * 导入：`Import -> General -> Existing Projects into Workspace`
    > * 导出：`Export -> General -> Existing Projects into Workspace`

1. **创建工作集**
    > * 可将相关的多个 Java 项目放在一起管理
    > * 设置工作集名，添加项目至工作集：`File -> New -> Java Working Set`
    > * 新建 java 项目时，可在对话框中设置添加到已存在的工作集中
    > * 可在 Package Explorer 视图的右上角：倒三角形（View Menu）进行管理工作集

1. **两个控制台视图**
    > * `Console` 视图 → `Open Console`（选择：`New Console View`）

1. **Javadoc**
    > * 光标定位于文档注释区域，可在 Javadoc 视图中预览效果
    > * 产生Javadoc：`项目右击 -> Export -> Java -> Javadoc`
    > * javadoc 生成出现错误 “编码 GBK 的不可映射字符”：
    >   * 解决方法：最后一步中VM设置行中加入代码 : `-encoding utf-8 -charset utf-8`

1. **命令行参数**
    > 1. 右键：`Run As -> Run Configurations -> 双击 Java Application`
    > 1. 右边选择：`Arguments 选项卡 -> Program arguments`（多个参数以空格分隔）

1. **管理源代码**
    > * 可以使用多个 Source Folder 存放源代码，适合将功能代码与测试代码分开
    > * 项目右击新建 Source Folder，此 Source Folder 将与 src 目录处于同一地位，可存放测试代码

1. **书签与任务标签**
    1. **书签**
        * Bookmark：用于记录代码的某行，方便管理与定位代码
        * 编辑区最左边右击：Add Bookmark...
        * 打开 Bookmarks 视图

    1. **任务标签**
        * 一种特殊的注释，有助于提高开发效率和代码管理
            > * `TODO`：指此处需要实现某功能
            > * `FIXME`：一般指此处逻辑错误或有异常，待处理
            > * `XXX`：一般指此处功能已实现，但待优化，待商榷
        * 打开 Tasks 视图

# 4. 【重构】
> * 方式1. Refactor 菜单
> * 方式2. 右击选择 Refactor => `Alt + Shift + T`

1. **重命名**：`Rename` => `Alt + Shift + R`
1. **移动**：`Move` => 移动文件位置，其实直接拖动至目标位置更方便
1. **更改方法签名**：`Change Method Signature` => 可修改方法的修饰符、返回值、方法名、形参
1. **提取方法**：`Extract Method` => `Alt + Shift + M`
1. **提取局部变量**：`Extract Local Variable` => 选中常量值右键操作
1. **提取常量**：`Extract Constant` => 选中常量值右键操作
1. **转换局部变量为域**：`Convert Local Variable to Field` => 选中变量名右键操作，变量由局部变类成员
1. **转换匿名类为嵌套类**：`Convert Anonymous Class to Nested Class` => 选中匿名类后右键操作
1. **移动类型为新文件**：`Move Type to New File` => 在有多个类的文件中，选中非public类右键操作
1. **内联**：`Inline Method` => 选中调用方法名操作，即用方法体的内容代替方法调用
1. **引入工厂**：`Introduce Factory` => 选中构造器右键操作
1. **引入参数**：`Introduce Parameter` => 选中表达式变量，右键操作，结果将会添加形参，该表达式变量由生成的形参代替
1. **泛化声明类型**：`Generalize Declared Type` => 选中对象变量，右键操作，该变量类型将变为父类型（多态运用）

# 5. 【提升性能的几个技巧】
1. 关闭不使用的项目
1. 移除所有在启动时加载的插件: `General > Startup and Shutdown`
1. 禁用拼写检查: `General > Editors > Text Editors > Spelling`（取消勾选 Enable spell checking）
1. 关闭验证: `Validation` → 勾选 `Suspend all validator`
1. 移除所有用不到或不想用的内容（尽量使用快捷键）`Window → Customize Perspective`
1. `Install/Update → Automatic Updates` → 取消勾选 `Automatically find new updates and notify me`
