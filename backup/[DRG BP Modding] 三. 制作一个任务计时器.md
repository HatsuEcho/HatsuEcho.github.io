在个人文件夹下, 创建任务计时器文件夹.

![Image](https://github.com/user-attachments/assets/22fd6d6e-3d73-4236-b73c-62d22d6a05c5)

进入该文件夹, 右键创建用户控件蓝图.

![Image](https://github.com/user-attachments/assets/7e73e362-d7fa-4360-83ea-c0b74cf13aa7)

![Image](https://github.com/user-attachments/assets/ce236148-487f-43c6-883a-dfeb287ce5e1)

打开控件蓝图, 在左侧将文本块拖入画布面板中

![Image](https://github.com/user-attachments/assets/ac98721d-dcd0-4db6-bc21-6481952a87cd)

锚点设置为顶部居中

![Image](https://github.com/user-attachments/assets/df2f7b19-626f-4cd0-b4bb-447e4744f49a)

并按照图中调整属性

![Image](https://github.com/user-attachments/assets/aeeef444-44eb-4bfa-bbeb-dddbea3f0b9a)

字体尺寸可以根据情况适当调整.
接着修改文本块的命名, 设置为变量.

![Image](https://github.com/user-attachments/assets/dc9241ca-bbaa-4faf-87da-bf34e3acaada)

回到文件夹, 再创建一个用户控件蓝图, 用于该 Mod 的设置界面.

![Image](https://github.com/user-attachments/assets/8c6ef87a-b375-4408-a2d7-834abcfe8f65)

设置界面可随意设计, 只需确保你拥有勾选框, 并且设为变量.

![Image](https://github.com/user-attachments/assets/cf9f5451-0de0-497d-a979-4fcdfb5b524f)

![Image](https://github.com/user-attachments/assets/905a9f65-9043-416d-9c6a-74ff1b44f0d8)

在文件夹内创建一个蓝图类, 类选择SaveGame.

![Image](https://github.com/user-attachments/assets/d1a59e0b-d3d2-4cc0-9b0c-38e5472d0b2d)

这会作为我们 Mod 的存档, 可以将需要保存的参数和设置保存到硬盘.
打开存档蓝图, 创建一个布尔值变量.

![Image](https://github.com/user-attachments/assets/550faf96-b71c-42a6-934e-13c40cdd086d)

然后回到文件夹, 接下来创建 Mod 的主要蓝图, 类型为 Actor.

![Image](https://github.com/user-attachments/assets/a2f9abff-908c-4ecd-be12-6622e15f9e41)

关闭启用 Tick 和可被伤害.

![Image](https://github.com/user-attachments/assets/d1bc18c6-cff5-4553-9732-2d987efc02b7)

按照下图编写蓝图逻辑.

![Image](https://github.com/user-attachments/assets/890878cf-9657-46fc-9871-2963a97a7435)

你可能会好奇为什么每次都要循环查找本地玩家, 这么做的原因是确保当前不处在加载阶段, 并且许多涉及到玩家的变量需要获取有效的玩家数据.
创建一个自定义事件, 随意命名. 你可以从左边事件拖出, 连接在前面的节点后执行, 并启用 Tick.

![Image](https://github.com/user-attachments/assets/4a10e92b-7fb1-4178-ac2d-0d54b0369caa)

在主要事件中, 使用序列节点, 先从路径加载存档, 路径可参考下图.

![Image](https://github.com/user-attachments/assets/7240e998-6e21-4ae8-8bb7-dfb2fcee4471)

判断有效性后 Cast 到存档蓝图, 若成功则设为变量, 无效或失败则创建对应存档.

![Image](https://github.com/user-attachments/assets/ae8975e8-cb2a-40c9-8e6f-4b8492d70b19)

之后创建设置界面 Widget.

![Image](https://github.com/user-attachments/assets/710d404e-a78a-4ee7-880e-1eba54be2616)

切换到设置界面蓝图图表, 创建一个变量, 变量类型为刚才创建的存档蓝图, 并且勾选可编辑实例和生成时公开.

![Image](https://github.com/user-attachments/assets/4e2404be-6ca9-404a-9425-c6370034999e)

回到主蓝图, 右键刷新节点, 就会看到存档的输入, 将存档连接到输入中.

![Image](https://github.com/user-attachments/assets/faa81c8c-3024-4d51-9086-1c1924a3713f)

![Image](https://github.com/user-attachments/assets/7d1754f3-b61b-48a8-ae0d-9ab5137be55a)

继续创建计时器的小部件.

![Image](https://github.com/user-attachments/assets/935f3f49-b7cb-4890-b32e-4a88107312dc)

切换到设置界面蓝图图表, 在事件构造设置勾选框状态.
从存档读取上一次 Mod 的开关.

![Image](https://github.com/user-attachments/assets/ba93d32e-af07-4688-a212-7616fae87832)

当然每一次开关的状态也要保存到存档中.

![Image](https://github.com/user-attachments/assets/81c67975-f5b8-433b-9ba2-5228d72e026b)

![Image](https://github.com/user-attachments/assets/4f40f715-6cdb-4592-b883-6d29a439725a)

在主蓝图中, 还是从存档获取开关状态决定是否将小部件显示到画面中.

![Image](https://github.com/user-attachments/assets/f0d96272-c7d4-461a-b7b9-cd2642244991)

在设置界面蓝图里创建事件分发器, 并添加布尔值输入, 然后将事件拖到图表, 选择调用.
这里的作用是当勾选框被勾选或取消时, 通过事件分发器告诉某蓝图, 以执行某些节点.

![Image](https://github.com/user-attachments/assets/b7a0f559-7b8d-41e0-b63a-4c18d584c159)

![Image](https://github.com/user-attachments/assets/6da51b7c-0a8f-40f6-a9fb-ded7112659da)

别忘了在主蓝图中绑定这个事件.

![Image](https://github.com/user-attachments/assets/a11ec68c-f37e-449a-843b-be1339560e5c)

![Image](https://github.com/user-attachments/assets/1eda009d-66a8-4035-a3db-c9a309cae3f6)

创建一个浮点值变量, 这里命名为 Time.

![Image](https://github.com/user-attachments/assets/525c7471-f493-4c73-96ad-7662d217a966)

在 Tick 事件中每帧对前一帧间隔相加, 就能得到累计的时间.

![Image](https://github.com/user-attachments/assets/e1836081-805e-4a2c-81db-6238b5c78b23)

再创建一个字符串变量, 并按下图对时间做简单的计算, 通过合并节点, 即可得到标准时间格式.

![Image](https://github.com/user-attachments/assets/a161b35f-4736-4483-9d19-8d407047a404)

然后设置小部件显示的文字.

![Image](https://github.com/user-attachments/assets/effe97dc-fd32-4f4e-8f33-3a1df94454c0)

到这里主要的逻辑就写好了, 但还有一些小设置需要做, 那就是将 Mod 设置界面绑定到 ModHub 中.
先在设置界面蓝图图表上方点击类设置, 在左侧面板添加 IHub Page Widget 接口.

![Image](https://github.com/user-attachments/assets/47c6032b-014d-4578-bc59-fe2a66217543)

在接口里双击第一个函数, 页面的名称根据自己情况填写.

![Image](https://github.com/user-attachments/assets/807cee4f-3e30-4ad3-90ef-6b57c701f6a8)

![Image](https://github.com/user-attachments/assets/571ffd4e-183f-460b-a362-0f7853d4ad2c)

接着回到主蓝图, 同样需要添加接口, 选择 IHub Mod.

![Image](https://github.com/user-attachments/assets/6ce3dfe1-1876-47c4-a0ee-0f3e7505666c)

按下图设置信息.

![Image](https://github.com/user-attachments/assets/3a4c371a-5c85-4517-9e86-80907a38d71f)

![Image](https://github.com/user-attachments/assets/4e5a0518-5db2-4a51-8ced-7840eb662c2b)

注意, 如果设置界面UI无法连接到 Hub Pages, 请检查设置界面蓝图是否正确添加接口.
最后在主蓝图设置保存逻辑.
ModHub 关闭事件需要从左边接口的事件中右键选择实现事件得到.

![Image](https://github.com/user-attachments/assets/2bf5f4f6-37f9-4b2b-9db1-d5588feeca08)

![Image](https://github.com/user-attachments/assets/259271ff-20f5-4a21-9eb1-c2d3a9c30f86)

至此整个 Mod 就完成了, 这里我只需要在洞穴加载.

![Image](https://github.com/user-attachments/assets/bfb7d7f7-38f8-4d84-ad74-2aef3ffc469e)

打包方法与前一张相同, 不再赘述, 最后到游戏里看看效果吧.

![Image](https://github.com/user-attachments/assets/68cdaf71-cbe6-4c29-8d7c-04ee55d5bf91)

![Image](https://github.com/user-attachments/assets/39751c30-72d3-4960-931e-6847a8c0e5a1)

最后, 你的 Mod 存档会在这里.

![Image](https://github.com/user-attachments/assets/c84920c6-4961-4392-8ba8-274eea39eaf5)