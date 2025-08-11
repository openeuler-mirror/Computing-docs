# Usage Instructions

## Overview

- Root permissions are required for using and configuring sysBoost.
- Only one sysBoost instance can exist.
- The system administrator must ensure the configuration file is correct.

## Configuration

### Configuration File Description

Configuration file directory: **/etc/sysboost.d/**

**Table 1**  Client YAML configuration file

<a name="table114320101924"></a>

<table><thead align="left"><tr id="row84321410123"><th class="cellrowborder" valign="top" width="16.84%" id="mcps1.2.5.1.1"><p id="p7432201016216"><a name="p7432201016216"></a><a name="p7432201016216"></a><strong id="b643212101122"><a name="b643212101122"></a><a name="b643212101122"></a>Item</strong></p>
</th>
<th class="cellrowborder" valign="top" width="19.97%" id="mcps1.2.5.1.2"><p id="p54328101323"><a name="p54328101323"></a><a name="p54328101323"></a><strong id="b94321810524"><a name="b94321810524"></a><a name="b94321810524"></a>Description</strong></p>
</th>
<th class="cellrowborder" valign="top" width="15.72%" id="mcps1.2.5.1.3"><p id="p20432191016216"><a name="p20432191016216"></a><a name="p20432191016216"></a><strong id="b243212101218"><a name="b243212101218"></a><a name="b243212101218"></a>Type</strong></p>
</th>
<th class="cellrowborder" valign="top" width="47.47%" id="mcps1.2.5.1.4"><p id="p3432171020211"><a name="p3432171020211"></a><a name="p3432171020211"></a><strong id="b134321910621"><a name="b134321910621"></a><a name="b134321910621"></a>Value Range</strong></p>
</th>
</tr>
</thead>
<tbody><tr id="row104321010525"><td class="cellrowborder" valign="top" width="16.84%" headers="mcps1.2.5.1.1 "><p id="p17432141014217"><a name="p17432141014217"></a><a name="p17432141014217"></a>elf_path</p>
</td>
<td class="cellrowborder" valign="top" width="19.97%" headers="mcps1.2.5.1.2 "><p id="p1443261017218"><a name="p1443261017218"></a><a name="p1443261017218"></a>ELF file to be combined</p>
</td>
<td class="cellrowborder" valign="top" width="15.72%" headers="mcps1.2.5.1.3 "><p id="p2432010828"><a name="p2432010828"></a><a name="p2432010828"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="47.47%" headers="mcps1.2.5.1.4 "><p id="p143215103213"><a name="p143215103213"></a><a name="p143215103213"></a>ELF path supported by sysBoost</p>
</td>
</tr>
<tr id="row104321010525"><td class="cellrowborder" valign="top" width="16.84%" headers="mcps1.2.5.1.1 "><p id="p17432141014217"><a name="p17432141014217"></a><a name="p17432141014217"></a>mode</p>
</td>
<td class="cellrowborder" valign="top" width="19.97%" headers="mcps1.2.5.1.2 "><p id="p1443261017218"><a name="p1443261017218"></a><a name="p1443261017218"></a>sysBoost running mode</p>
</td>
<td class="cellrowborder" valign="top" width="15.72%" headers="mcps1.2.5.1.3 "><p id="p2432010828"><a name="p2432010828"></a><a name="p2432010828"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="47.47%" headers="mcps1.2.5.1.4 "><p id="p143215103213"><a name="p143215103213"></a><a name="p143215103213"></a>"static"</p>
</td>
</tr>
<tr id="row16432310326"><td class="cellrowborder" valign="top" width="16.84%" headers="mcps1.2.5.1.1 "><p id="p17432191018213"><a name="p17432191018213"></a><a name="p17432191018213"></a>libs</p>
</td>
<td class="cellrowborder" valign="top" width="19.97%" headers="mcps1.2.5.1.2 "><p id="p243217101521"><a name="p243217101521"></a><a name="p243217101521"></a>Dependency library of the ELF file specified by <strong>elf_path</strong>. This is optional because sysBoost can automatically detects dependency libraries.</p>
</td>
<td class="cellrowborder" valign="top" width="15.72%" headers="mcps1.2.5.1.3 "><p id="p543211018210"><a name="p543211018210"></a><a name="p543211018210"></a>String</p>
</td>
<td class="cellrowborder" valign="top" width="47.47%" headers="mcps1.2.5.1.4 "><p id="p1343231017218"><a name="p1343231017218"></a><a name="p1343231017218"></a>Path of the dependent library of the ELF file supported by sysBoost</p>
</td>
</tr>
</tbody>
</table>

### Configuration Example

sysBoost TOML configuration file example:

```text
# /etc/sysboost.d/bash.toml
elf_path = "/usr/bin/bash"
mode = "static-nolibc"
libs = ["/usr/lib64/libtinfo.so.6"]
```

## Usage

- Start sysBoost.

    ```text
    systemctl start sysboost.service
    ```

- Stop sysBoost.

    ```text
    systemctl stop sysboost.service
    ```

- Query sysBoost status. If there is no text in red, sysBoost is running normally.

    ```text
    systemctl status sysboost.service
    ```

- View logs. If sysBoost fails, see the system logs for details.

    ```text
    cat /var/log/messages
    ```
