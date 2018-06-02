SSH 相关配置
==============

<span id="add-to-ssh-agent">Adding your SSH key to the ssh-agent</span>
----------------------------------------------------------------------

Before adding a new SSH key to the ssh-agent to mange your keys, you should have
checked for existing SSH keys and generated a new SSH key.

1. Start the `ssh-agent` in the backgroud.
```bash
$ eval "$(ssh-agent -s)"
Agent pid 59566
```
2. Add your SSH private key to the `ssh-agent`. If you created your key with a different name, or if you are adding an existing key that has a different name, replace `id_rsa' in the command with the name of your private key file.

```bash
$ ssh-add ~/.ssh/id_rsa
```
3. Add the SSH key to your GitHub account.

FAQ
---

### `sign_and_send_pubkey`: signing failed: agent refused operation

触发条件：在服务器添加完公钥后，执行 `ssh` 命令登录服务时，报该错误

解决方案：[Adding your SSH key to the ssh-agent](#add-to-ssh-agent)

执行如下命令:
```bash
eval "$(ssh-agent -s)"
ssh-add
```


