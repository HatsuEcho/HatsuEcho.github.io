这次要做的 Mod 会相对有趣一些, 但同时比较麻烦, 需要使用一些特殊手段, 请务必严格按照教程来做.
前面的步骤就不解释了, 如果你从前面几章看下来, 基本都知道要做什么.

![Image](https://github.com/user-attachments/assets/e7cf4344-3ccb-48dd-8777-a2c69d8af7ee)

![Image](https://github.com/user-attachments/assets/1c1e092d-3bd9-4f7c-8fde-efb963e1a56f)

打开蓝图, 把父类改成玩家控制器.

![Image](https://github.com/user-attachments/assets/959bb825-95eb-455c-b902-fc77330c73ed)

随便放置一个节点, 比如这个.

![Image](https://github.com/user-attachments/assets/b2536f3c-3be9-4174-a2ed-a8bb6b6bbbf3)

然后随便找个地方右键新建关卡.

![Image](https://github.com/user-attachments/assets/2332114d-2940-4015-91ee-a1bf8639a421)

在左上角编辑, 项目设置, 左边选择地图和模式, 将地图设为刚才新建的关卡.

![Image](https://github.com/user-attachments/assets/9e5e75d7-46cf-4cf9-8d23-8d2ef7662cd3)

然后重启一下引擎.
打开关卡蓝图.

![Image](https://github.com/user-attachments/assets/e730d3d1-ba96-4e38-9670-7e95816c813b)

放置该节点.

![Image](https://github.com/user-attachments/assets/7ab9543b-e41e-41a5-9c17-a59e184e590f)

复制主蓝图的引用.

![Image](https://github.com/user-attachments/assets/2dc58cf3-ea9e-410f-87af-c6f324727b14)

把长引用粘贴到节点中, 并且去掉前面和后面多余的的内容, 看起来像这样.

![Image](https://github.com/user-attachments/assets/620011cc-e121-4986-a54a-fe8f10d20566)

回到主蓝图, 右键复制这个节点, 然后粘贴到记事本中.

![Image](https://github.com/user-attachments/assets/462ea549-9846-47c5-b4fb-da9f525c0bac)

在该节点后面继续添加 `:EventGraph.` .

![Image](https://github.com/user-attachments/assets/0458ac7c-0059-44c1-9c7f-121c9e20f3b4)

然后在记事本中找到这个节点在编辑器中的名称, 复制粘贴到节点后方.

![Image](https://github.com/user-attachments/assets/8d457d11-2532-4652-885f-af4de2ed5211)

![Image](https://github.com/user-attachments/assets/9dbef1d8-22d5-42fc-95c8-700d85ddb35d)

然后依次放置这些节点.

![Image](https://github.com/user-attachments/assets/f4d52d98-6307-4bd1-a6f5-b2b1b0c5eeaf)

![Image](https://github.com/user-attachments/assets/479b6b9c-4e55-4c97-a5c7-77f2123055f4)

接着在文件夹中新建蓝图函数库.

![Image](https://github.com/user-attachments/assets/8a137cb3-4840-45c0-9173-59834fccd8cf)

![Image](https://github.com/user-attachments/assets/512063a7-d306-401e-acc2-9680cba2a5a7)

在函数库里新建这两个函数, 名字必须跟图中一样, 然后不要点保存.

![Image](https://github.com/user-attachments/assets/21ed31db-0d30-4fb3-bb6b-f8ff52026f6a)

到关卡蓝图中调用这两个函数.

![Image](https://github.com/user-attachments/assets/d0359fb1-4970-459e-82ad-f58462256937)

保存好所有内容, 但是不要保存刚才新建的函数库, 然后关闭引擎重新打开.

![Image](https://github.com/user-attachments/assets/2958d3e0-3d77-4779-b1be-4e4895ccaafe)

忽略错误信息, 打开关卡蓝图, 可以看到, 这两个被人为隐藏的函数通过这种方法诱导出来了.
对这个函数填上变量值.

![Image](https://github.com/user-attachments/assets/cad0e3d8-7d02-42b9-a81b-36837ccebf6a)

然后新建一个变量, 类型为命中结果.

![Image](https://github.com/user-attachments/assets/262c3e8e-9447-4b43-a4b8-6bb1b80a6b3e)

选中该变量, Ctrl + C 复制粘贴到记事本中.

![Image](https://github.com/user-attachments/assets/07de774b-debf-481c-96d9-7bf06c4226d2)

找到图中这一个字段, 将 `HitResult` 修改为 `MemberReference` .

![Image](https://github.com/user-attachments/assets/7682cf4a-8177-4894-bb71-7240b98daa9a)

![Image](https://github.com/user-attachments/assets/b31437b5-f458-4750-8a13-d4db0959ed9c)

然后把刚才粘贴的这一整段复制, 回到编辑器, 粘贴变量.

![Image](https://github.com/user-attachments/assets/090c432a-ce38-45b2-909d-72109f4686c4)

![Image](https://github.com/user-attachments/assets/9f490e22-72a0-4562-87cc-b20e8b2b71d7)

继续复制该变量的默认值, 粘贴到记事本.
找到这一段, 填上 `ServerChangeName` .

![Image](https://github.com/user-attachments/assets/04c88249-0e65-4f7e-b953-abbb181c008c)

![Image](https://github.com/user-attachments/assets/6e98f5e8-8ffa-4db7-b299-c65265bba1f7)

复制主蓝图的引用, 替换这一段, 并掐头去尾, 在尾部加上 `_C` .

![Image](https://github.com/user-attachments/assets/70c9dbdf-d771-4099-bdc4-2d31e59f4cf9)

![Image](https://github.com/user-attachments/assets/34286f23-6c3b-4817-b8da-fb7461ec4be1)

![Image](https://github.com/user-attachments/assets/39093d0f-a338-41b5-9089-5b106d91e479)

接着复制这一段, 粘贴到变量的默认值.

![Image](https://github.com/user-attachments/assets/142b7d8b-9059-441f-ab18-fd636d2508a2)

把节点连接上, 编译保存.

![Image](https://github.com/user-attachments/assets/2aa8aa65-e1a8-4ca4-b8d4-a6c1ab2b446d)

然后运行该关卡, 等待1-2秒后关闭.

![Image](https://github.com/user-attachments/assets/8080ce84-6b52-42d5-8797-0bb2cf5f6159)

打开主蓝图, 右键刷新节点, 可以看到原本的节点已经被我们篡改成这个被隐藏起来的节点, 但我们并不能通过编译, 因为该节点被人为设置成不允许调用.

![Image](https://github.com/user-attachments/assets/c72fc17a-e141-4860-bf92-0f2d82eb4d41)

我们先断开这个节点的连接.
回到关卡蓝图, 连上第二个函数, 并填写好变量信息.

![Image](https://github.com/user-attachments/assets/ad052a36-4474-412a-bbec-afa9e4657694)

然后再运行一次关卡, 退出, 这时可以看到, 节点已经成功通过编译了!

![Image](https://github.com/user-attachments/assets/e19cc79b-d788-4ce0-8c62-a68ee530fcf0)

还没完, 记得把主蓝图的父类改回actor.
改回actor后, 就可以开始写你的 Mod 了.

![Image](https://github.com/user-attachments/assets/42c72a55-f3b3-4324-a978-532848d73906)

![Image](https://github.com/user-attachments/assets/d881c13a-94dc-4c6b-881c-73bc183e5015)

最后记得删掉关卡蓝图的内容.

![Image](https://github.com/user-attachments/assets/fc4cb8f3-b787-4ec6-811f-94a9ef182664)