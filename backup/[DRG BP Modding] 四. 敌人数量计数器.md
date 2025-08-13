这一节我们将继续深入, 制作一个敌人数量计数器.
先说下核心思路, 我们需要找到场景中所有属于敌方的角色, 然后按照蜂拥敌人, 静止敌人, 常规敌人来分类, 最后将每一个分类的敌人数量显示在屏幕上.
那么现在开始动手.
按照惯例, 创建文件夹, 以及所需的存档, 用户界面等.

![Image](https://github.com/user-attachments/assets/383234f6-58b1-4bda-8f5e-9dafc768dd34)

![Image](https://github.com/user-attachments/assets/484cfabf-6547-4eed-bdf3-b5fb8658b16f)

在存档中创建布尔值变量, 这些步骤与上一章基本相同.

![Image](https://github.com/user-attachments/assets/f6752473-80a8-478c-bc2d-1fff91527d65)

然后在计数器界面中设置好样式.
别忘了把对应的三个文本块设成变量.

![Image](https://github.com/user-attachments/assets/18c9d97d-3546-4a42-997b-d66d66e184c5)

![Image](https://github.com/user-attachments/assets/53dc79ab-8da8-4bb6-a978-b1c412bd0661)

设置界面也一样, 确保勾选框是变量即可.

![Image](https://github.com/user-attachments/assets/13e38222-b676-4a9e-a6b1-75147f805948)

![Image](https://github.com/user-attachments/assets/d8699e03-e6ae-4117-a4c9-548fa9e4a9a3)

现在开始创建主要蓝图 Actor.
按照惯例去掉可被伤害, 编写好准备阶段的逻辑.
这里的1秒延迟主要是防止某些偶然情况小部件过早添加到视口导致无法显示在屏幕上.

![Image](https://github.com/user-attachments/assets/140a32e4-bcdd-4aa8-abf5-a59c132e4034)

![Image](https://github.com/user-attachments/assets/c433ccf7-4e04-4f33-bead-343890ec95d6)

![Image](https://github.com/user-attachments/assets/8fa06297-5b7d-4c36-852d-572059295143)

设置界面的输入别忘了添加.

![Image](https://github.com/user-attachments/assets/036a00b0-705e-4405-9342-3ca985e4b020)

![Image](https://github.com/user-attachments/assets/3523afc9-1a5b-44f9-af40-b0a5b0571ede)

初始化步骤完成之后, 到设置界面实现勾选框的功能.

![Image](https://github.com/user-attachments/assets/82fe6b19-1b1a-4297-a8d1-337b9e19bb14)

之后到主蓝图回应这个事件.

![Image](https://github.com/user-attachments/assets/3cd623df-2692-4e31-926d-f1b9d4a875c3)

然后现在开始编写这个 Mod 的主要功能了, 创建一个函数, 使用定时器去获取场景的敌人并且将数量更新到小部件上.

![Image](https://github.com/user-attachments/assets/b66af62a-1ab5-426e-a400-621cb2c3631b)

![Image](https://github.com/user-attachments/assets/89c72007-bef1-4339-9e91-350c6a87c7bc)

这里我选择获取场景中所有含有敌对标签的 FSDPawn 类, 创建一个 FSDPawn 类的集合, 将获取到符合条件的敌人都放进去.

![Image](https://github.com/user-attachments/assets/29429033-7044-448f-97a7-47207f7cf420)

创建一个函数, 按下图添加输入, 这一步将用于获取蜂拥类敌人.

![Image](https://github.com/user-attachments/assets/c61be40d-f058-4b77-a2fc-c528b6c63141)

![Image](https://github.com/user-attachments/assets/104d5147-44ea-4d06-ba2e-be234babd1ea)

在该函数中, 对输入的敌人输出到一个数组, 使用 For Each Loop 节点遍历这个数组.
我们首先需要知道, 游戏中绝大多数可移动的敌人, 都在 EnemyDeepPathfinderCharacter 类下, 而静止类敌人处于 EnemyPawn 类下, 所以需要将符合条件的筛出来.

![Image](https://github.com/user-attachments/assets/f9500e31-9641-4918-a17c-6763ea7842f2)

用分支节点判断每个敌人是否含有敌对和蜂拥标签, 这样就能筛选出所有的蜂拥类敌人.

![Image](https://github.com/user-attachments/assets/2c03eb40-c574-4db2-a213-1398128d84ae)

创建一个映射, 将所有不在键集中的敌人都添加进去.

![Image](https://github.com/user-attachments/assets/4a5a5753-fc48-4832-b79c-fe5021844a90)

![Image](https://github.com/user-attachments/assets/b4622865-bbe4-40e9-af79-1903d11dc0cf)

但还没完, 在这个过程中, 也会有很多敌人死亡, 或者被系统刷掉, 对于这些已经无效的敌人我们要及时移除.
在数组遍历完成后, 继续检查映射中的敌人, 通过健康组件判断是否已经死亡或者无效, 然后从映射中移除.

![Image](https://github.com/user-attachments/assets/f57dc97f-d14f-457a-ac75-b7e1401db3a5)

剩下的静止类敌人和常规敌人也是一样的思路.

![Image](https://github.com/user-attachments/assets/31627cd5-4c10-4cf8-b398-d27831b93df2)

![Image](https://github.com/user-attachments/assets/e983277f-ff7c-4834-98b2-27fb337083fb)

![Image](https://github.com/user-attachments/assets/3a62f5e7-6b54-4f2b-a9e6-6330967c4222)

等到具体的敌人之后, 我们只需要分别获取每个映射的长度就能得到敌人的数量, 这里再创建一个函数来处理.

![Image](https://github.com/user-attachments/assets/711d4cda-a6ad-4fe4-8580-c4def34420e4)

按照下图将长度转换成字符, 经过处理后设置为小部件对应的文本内容.

![Image](https://github.com/user-attachments/assets/0722c4d9-2a98-42d2-a75b-aaedaa50a492)

剩下的步骤都是一样的.

![Image](https://github.com/user-attachments/assets/0715b78c-0301-4cbc-a405-4f6d6f1902c9)

到这里 Mod 的功能已经全部完成了, 像以往一样添加 ModHub 的接口就行.

![Image](https://github.com/user-attachments/assets/6e584a22-7916-4db5-92f4-1e883c3fd5d6)

![Image](https://github.com/user-attachments/assets/2b2b12b5-34eb-42e8-86e0-2e6ee2ba8a0f)

![Image](https://github.com/user-attachments/assets/2297a8f9-377d-45b5-90be-238f9526c66a)

以及保存存档.

![Image](https://github.com/user-attachments/assets/6456b10a-b227-412d-9bc3-2b91a30be154)

检查无误后就可以打包了.

![Image](https://github.com/user-attachments/assets/0d995c13-9278-40e0-b06a-fd9435e7520a)

进游戏看看效果.

![Image](https://github.com/user-attachments/assets/68ccaba1-4142-4445-a577-bddc6fc750e1)