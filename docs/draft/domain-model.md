# 领域模型
## 类图
```
                      +------------+
                      | LocalAsset |
                      +-----+------+
                            |

                 +-------+1 |  +----------+
                 | Asset +--+--+ Register |
                 +-------+     +-----+----+
                    1|               |
                     |1
                +---------+          |        +--------+
                |         +----------+--------+        |
                | Account |                   | Device |
                |         +----------+--------+        |
                +-+-----+-+          |        +--------+
                  |     |
                  +--+--+            |
                     |
                                     |
                     |
+---------+     1+---+----+          |
| Message +------+ Dialog |
+---------+      +---+----+          |
                     |
                     |               |
              +------+------+   +----+----+
              | LocalDialog +---+ Session |
              +-------------+   +---------+

```
不连续的线为虚线，连接着关联类和关联线。

除标注为1的地方，关联多重性都为*。

Asset为Account拥有的资产（理论上的，即时的，完整的）。Device在注册Account后，在本地保存其Account当时的Asset，即LocalAsset。

Dialog为具体两个Account之间的对话（理论上的，即时的，完整的）。Device根据需要，在本地保存部分Account之间的部分Dialog，即LocalDialog。

Account在登录Device产生Session后，可以打开部分LocalDialog。

### 类结构
#### Dialog
方法：
- addMessage
- removeMessage
- createMessage
- mergeDialog
- on以上方法
- getMessages

## 组件
### Register Manager
- registerAccount //注册一个现有的Account
- removeAccount
- createAccount
- authenticateAccount
- on以上方法（如onRegisterAccount ）
- getAccount

### LocalDialog Manager
- createDialog
- removeDialog
- on以上方法
- getDialog

### Session Manager
- createSession
- deleteSession
- loginAccount
- logoutAccount
- on以上方法
- getSessions
