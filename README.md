# -Q-CuGAN-QQ-
采用python和CuGAN模型实现超分辨率QQ机器人，可以随心所欲地在QQ平台对低清动漫图片进行修复及超分
超分辨率机器人框架采用酷Q的HTTP框架处理QQ信息，python采用Flask搭建后端，
其中超分辨率模型是CuGAN模型，只适用于二次元图像的修复，项目地址：https://github.com/bilibili/ailab
使用方法：
1.注册一个QQ小号，将该QQ号拉入你希望提供服务的群聊中。
2.修改config.yml配置文件，在前两行输入你的QQ账号和密码，如果不输入密码可以进行扫码登陆。
3.登录 https://sm.ms/ 网站，申请一个免费的图床，将校验密钥填入post.py文件第193行的Authorization参数后。
4.先用jupyter打开QQRobot.ipynb，运行第一个单元格。
5.接着双击运行go-cqhttp.bat文件即可。注意要保证网络联通。
6.退出QQ小号，用您的其他账号在机器人所在的群聊中发送"超分辨率"（不包括冒号）以及一张需要做超分处理的图片，
请注意图片和”超分辨率“这四个字和图片应在一条消息内（即在同一个气泡内），仅支持单张图片处理，请不要发送多张图片。
7.稍等片刻即可得到机器人的反馈，两次指令发送的间隔不得小于五秒钟，您可以自行修改。
8.艾特机器人并跟上提问可以和机器人进行聊天，例如发送”@机器人 你叫什么名字呀？“，机器人会进行回复。

注意事项：
1.超分辨率模型需要一个强大的英伟达GPU才能运行，如果您没有GPU设备，
请在CUGAN.py文件中找到upscaler = RealWaifuUpScaler(3, ModelPath+ModelName, half=True, device="cuda:0")
将device参数修改为device='cpu'便可指定CPU进行计算，消耗时间可能会稍长一点。
2.在post.py文件第227行，我预先指定了两次超分辨率服务运行的最小间隔时间，小于5秒的指令会忽略，以防止计算机超载，
您可以根据您计算机的运算性能进行调整。
3.超分辨率模型需要消耗大量的显存，请确保您GPU的显存至少大于6GB。
4.聊天功能采用模板匹配的方法进行，可以自行增减语料库word.txt，但需要符合格式。
语料库以细胞为基本单位，第一行为用作匹配的提问模板，第二行为回复，第三行为关键词，第四行为补充回复，其中关键词和补充回复可为0。
语料库最后很多行0为语料库结束标志，请勿删除。
5.请预先安装pytorch和cuda以及jupyter，这方面请自行在网络上寻找教程。

有任何问题请联系开发者，BiliBili Uid：436636983 @GNK48-嘉兴塘小阳
