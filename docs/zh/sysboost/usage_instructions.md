# 使用方法

## 总体说明

- 使用和配置sysBoost需要使用root权限。
- sysBoost不支持多实例运行。
- 请管理员确保配置文件的正确性。

## 配置方法

### 配置文件说明

配置文件目录：/etc/sysboost.d/

**表 1**  客户端yaml文件配置说明

<a name="table114320101924"></a>

<table><thead align="left"><tr id="row84321410123"><th class="cellrowborder" id="mcps1.2.5.1.1" valign="top" width="16.84%"><p id="p7432201016216"><a name="p7432201016216"></a><a name="p7432201016216"></a><strong id="b643212101122"><a name="b643212101122"></a><a name="b643212101122"></a>配置名称</strong></p>
</th>
<th class="cellrowborder" id="mcps1.2.5.1.2" valign="top" width="19.97%"><p id="p54328101323"><a name="p54328101323"></a><a name="p54328101323"></a><strong id="b94321810524"><a name="b94321810524"></a><a name="b94321810524"></a>配置说明</strong></p>
</th>
<th class="cellrowborder" id="mcps1.2.5.1.3" valign="top" width="15.72%"><p id="p20432191016216"><a name="p20432191016216"></a><a name="p20432191016216"></a><strong id="b243212101218"><a name="b243212101218"></a><a name="b243212101218"></a>参数类型</strong></p>
</th>
<th class="cellrowborder" id="mcps1.2.5.1.4" valign="top" width="47.47%"><p id="p3432171020211"><a name="p3432171020211"></a><a name="p3432171020211"></a><strong id="b134321910621"><a name="b134321910621"></a><a name="b134321910621"></a>取值范围</strong></p>
</th>
</tr>
</thead>
<tbody><tr id="row104321010525"><td class="cellrowborder" headers="mcps1.2.5.1.1" valign="top" width="16.84%"><p id="p17432141014217"><a name="p17432141014217"></a><a name="p17432141014217"></a>elf_path</p>
</td>
<td class="cellrowborder" headers="mcps1.2.5.1.2" valign="top" width="19.97%"><p id="p1443261017218"><a name="p1443261017218"></a><a name="p1443261017218"></a>需要合并的可执行ELF文件的名称</p>
</td>
<td class="cellrowborder" headers="mcps1.2.5.1.3" valign="top" width="15.72%"><p id="p2432010828"><a name="p2432010828"></a><a name="p2432010828"></a>字符串</p>
</td>
<td class="cellrowborder" headers="mcps1.2.5.1.4" valign="top" width="47.47%"><p id="p143215103213"><a name="p143215103213"></a><a name="p143215103213"></a>sysBoost支持的可执行ELF文件路径名称</p>
</td>
</tr>
<tr id="row104321010525"><td class="cellrowborder" headers="mcps1.2.5.1.1" valign="top" width="16.84%"><p id="p17432141014217"><a name="p17432141014217"></a><a name="p17432141014217"></a>mode</p>
</td>
<td class="cellrowborder" headers="mcps1.2.5.1.2" valign="top" width="19.97%"><p id="p1443261017218"><a name="p1443261017218"></a><a name="p1443261017218"></a>sysBoost的运行模式</p>
</td>
<td class="cellrowborder" headers="mcps1.2.5.1.3" valign="top" width="15.72%"><p id="p2432010828"><a name="p2432010828"></a><a name="p2432010828"></a>字符串</p>
</td>
<td class="cellrowborder" headers="mcps1.2.5.1.4" valign="top" width="47.47%"><p id="p143215103213"><a name="p143215103213"></a><a name="p143215103213"></a>"static-nolibc"</p>
</td>
</tr>
<tr id="row16432310326"><td class="cellrowborder" headers="mcps1.2.5.1.1" valign="top" width="16.84%"><p id="p17432191018213"><a name="p17432191018213"></a><a name="p17432191018213"></a>libs</p>
</td>
<td class="cellrowborder" headers="mcps1.2.5.1.2" valign="top" width="19.97%"><p id="p243217101521"><a name="p243217101521"></a><a name="p243217101521"></a>elf_path所指定的可执行ELF文件的依赖库，sysBoost可以自动探测依赖库，故为可选项</p>
</td>
<td class="cellrowborder" headers="mcps1.2.5.1.3" valign="top" width="15.72%"><p id="p543211018210"><a name="p543211018210"></a><a name="p543211018210"></a>字符串</p>
</td>
<td class="cellrowborder" headers="mcps1.2.5.1.4" valign="top" width="47.47%"><p id="p1343231017218"><a name="p1343231017218"></a><a name="p1343231017218"></a>sysBoost支持的可执行ELF文件的依赖库的路径名称</p>
</td>
</tr>
</tbody>
</table>

### 配置示例

sysBoost的toml配置文件示例：

```sh
# /etc/sysboost.d/bash.toml
elf_path = "/usr/bin/bash"
mode = "static-nolibc"
libs = ["/usr/lib64/libtinfo.so.6"]
```

## 操作方法

- 启动sysBoost服务

    ```sh
    systemctl start sysboost.service
    ```

- 关闭sysBoost服务

    ```sh
    systemctl stop sysboost.service
    ```

- 状态查询（若没有标红字体，说明sysBoost运行正常）

    ```sh
    systemctl status sysboost.service
    ```

- 日志（若sysBoost出现错误，可通过系统日志查询相关信息）

    ```sh
    cat /var/log/messages
    ```
