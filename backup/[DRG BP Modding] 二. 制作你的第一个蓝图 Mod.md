按照上一章节的指引完成设置后, 双击 FSD-Template 文件夹下的 FSD.uproject 以打开引擎项目.

![Image](https://github.com/user-attachments/assets/727ca486-c7bb-48db-8de2-bbca26311cf1)

首次打开虚幻引擎, 界面应该与图中样式保持一致.

![Image](https://github.com/user-attachments/assets/5c1c31f5-a9ba-483d-823e-5497b8a9eea4)

现在正式开始制作第一个蓝图 Mod , 先来一个简单的角色闪现.
确保当前处于 Content (内容) 文件夹下, 右键新建文件夹.

![Image](https://github.com/user-attachments/assets/5a6e5431-27ca-4453-9868-f624d690fde5)

命名最好使用自己的 ID , 比如我会使用 "_HatsuEcho", 以避免与其他 Mod 路径重合.

![Image](https://github.com/user-attachments/assets/e8016cc5-3180-4aed-8444-4b62c68d0f37)

在该文件夹下继续创建单独 Mod 的文件夹, 我们想做闪现 Mod, 就可以命名为 "_Teleport".

![Image](https://github.com/user-attachments/assets/f72d45a0-dd6a-4d8e-91d4-71aeb89f1ae0)

在 _Teleport 文件夹下, 右键创建蓝图类.

![Image](https://github.com/user-attachments/assets/d0ca11fc-5a11-4da8-a54d-b7e6133b82b6)

类选择 Actor.

![Image](https://github.com/user-attachments/assets/b1d97e80-1183-4c5d-bea5-bb54ecf21edd)

填写 Mod 的名称.

![Image](https://github.com/user-attachments/assets/64e64fb7-68ec-4027-ae3f-0b92621b0a2e)

然后双击打开 Actor.

![Image](https://github.com/user-attachments/assets/81d0bfe8-728e-4637-b0f2-ec5ec6557e7a)

点击上方类默认值, 在右侧细节面板中把可被伤害选项取消勾选.

![Image](https://github.com/user-attachments/assets/23f5a597-fcfe-44c6-86d6-2b6d4dd7f47b)

点击事件图表选项页.

![Image](https://github.com/user-attachments/assets/0157c549-0d1a-4cb0-b005-d4298a7198c5)

引擎默认生成了三个事件节点, 我们只需要用到第一个 "Event BeginPlay" 事件, 所以可以把其余两个删掉, 左键框选节点, 按下 Delete 键即可删除.
按住右键拖动可以移动视图.
在空白区单击右键打开节点窗口, 输入 "Get Local Player Character", 选择该节点.

![Image](https://github.com/user-attachments/assets/625c28d4-8c9d-44ac-8f91-b6249b933326)

单击就会放置到图表中.

![Image](https://github.com/user-attachments/assets/49e7c513-412d-4ff4-a67d-9715f3528814)

这个节点是 DRG 游戏内的, 可以直接获取本地角色.
在 Event BeginPlay 事件后方按住左键并拖出执行引脚, 选择 Is Valid 节点.

![Image](https://github.com/user-attachments/assets/39955465-8597-4f4b-b0e1-eafa25d43bdd)

从 Get Local Player Character 节点的输出连接至 Is Valid 节点的输入中.

![Image](https://github.com/user-attachments/assets/701626a8-a739-460e-a99f-3956b48b052c)

此步骤用于检查获取的本地角色是否有效, 并且你应该包含一种解决方法来应对.
如下图所示, 在获取失败的情况下给予短暂延迟后继续尝试获取. 双击执行引脚可添加断点, 保持整洁的蓝图是良好的习惯.

![Image](https://github.com/user-attachments/assets/3dc0c52f-1032-47cf-8dc3-b5c41c782721)

我们希望通过按键操控闪现, 所以需要对 Mod 接收玩家控制器的输入.

![Image](https://github.com/user-attachments/assets/1ed8d257-5791-438e-95ba-fe6de21fa3c9)

完成后点击左上方的编译, 我强烈建议你将使用时保存设置为总是.

![Image](https://github.com/user-attachments/assets/7f2e123e-17f1-4ee4-8d32-4dc2f92d25de)

现在右键空白处输入 Key , 这里以 K 键为例.

![Image](https://github.com/user-attachments/assets/f0a981be-0e74-4e00-a27d-6b015b2a6d06)

先得到自己角色当前的位置.

![Image](https://github.com/user-attachments/assets/e340e60f-5b40-45be-ae19-673296ae49e8)

然后获取角色的旋转角度, 再得到当前视角朝向的向前向量.

![Image](https://github.com/user-attachments/assets/ab2f0df5-1b93-4bf0-af67-6cad68a71831)

![Image](https://github.com/user-attachments/assets/9aeb4496-d189-41fd-92dc-6d84ab8a255e)

将向前向量乘一个浮点值, 这个值就是你希望闪现的距离, 这里填写300, 也就是3米.

![Image](https://github.com/user-attachments/assets/e891d768-4d8c-4679-b810-21641dcfadad)

![Image](https://github.com/user-attachments/assets/14be08e8-149f-4fd3-887f-0e04a90b6e87)

然后将角色当前位置与闪现的距离相加, 这就是角色闪现之后的位置.

![Image](https://github.com/user-attachments/assets/c5b9ce15-015d-4ea4-86d7-a503404c9ab6)

![Image](https://github.com/user-attachments/assets/d1fe4e99-2ce1-4668-9350-e3cd8dbdaf9c)

然后使用 SetActorLocation 节点设置角色的位置, 并勾选 Sweep 布尔值, 防止闪现到其他物体内部.

![Image](https://github.com/user-attachments/assets/7fc7dd45-de5f-4b28-ade2-d24d749af631)

这样 Mod 的功能就完成了, 记得编译保存!

![Image](https://github.com/user-attachments/assets/34100dee-b981-4d40-b245-5b5e466e0c90)

回到文件夹里, 对该 Actor 右键创建子类蓝图, 并命名为 "InitSpacerig", 重复这个步骤, 再创建一个子类蓝图命名为 "InitCave".
InitSpacerig = Mod 会在太空站台加载.
InitCave = Mod 会在洞穴(任务开始)内加载.
如果不希望 Mod 在洞穴内生效, 则删除 InitCave, 反之亦然.

![Image](https://github.com/user-attachments/assets/e4bc2417-553c-4910-bff0-d268f9d8aa2f)

![Image](https://github.com/user-attachments/assets/1f0afff9-2ac9-46b7-9531-4ca5b6065862)

Ctrl+Shift+S 保存所有内容.
然后就可以打包你的 Mod 了.

![Image](https://github.com/user-attachments/assets/ee0ae001-2513-4528-bba3-677d90d558c8)

打包路径可以在任意地方, 我通常选择 FSD-Template 文件夹下.

![Image](https://github.com/user-attachments/assets/c1136e14-78a7-484e-9b33-6eb6fd7da48e)

然后引擎会开始编译, 首次编译会花费较长时间, 请耐心等待编译完成, 如遇到编译错误, 你需要点击显示输出日志, 检查所有 Error 信息并寻找解决办法.

![Image](https://github.com/user-attachments/assets/11900aa8-d018-45a4-9037-b1447d5020a6)

打包完成后, 将 DRGPacker.zip 解压, 你应该得到这些文件.

![Image](https://github.com/user-attachments/assets/c67a8d70-6671-46eb-b181-96f9d71a7150)

回到引擎打包路径, 找到 WindowsNoEditor\FSD 下的 Content 文件夹, 确保该文件夹内只含有你 Mod 的内容.

![Image](https://github.com/user-attachments/assets/6661fcf6-a887-4491-b9a4-2a0e28762fcc)

然后将 Content 复制到 DRGPacker 下的 Input_P 文件夹内.

![Image](https://github.com/user-attachments/assets/95723e55-3e79-4c37-92b4-4ba0113c3556)

左键单击并拖动 Input_P 文件夹到 _Repack 上, 生成的 .pak 就是你的 Mod 成品.

![Image](https://github.com/user-attachments/assets/1f55d01e-94ae-49ab-bece-aea22a113333)

![Image](https://github.com/user-attachments/assets/116566d3-e95c-4c83-bcba-4aaae1676fe5)

需要注意的是, 蓝图 Mod 需要放入 Mod 管理器或通过 Modio 订阅才能正常在游戏内加载.