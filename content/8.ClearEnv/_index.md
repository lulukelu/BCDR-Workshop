﻿---
title: "清理环境"
chapter: false
weight: 80
---

## 清理环境

完成所有实验以后，按照以下步骤清理环境：

1.清理DMS相关环境：

* 删除DMS任务，进入DMS任务控制台：https://cn-northwest-1.console.amazonaws.cn/dms/v2/home?region=cn-northwest-1#tasks
选中"dr-task"，在【操作】下拉菜单里选择"删除"选项。并在弹出窗口中点击【删除】按钮。

* 删除终端节点，在DMS终端节点控制台：https://cn-northwest-1.console.amazonaws.cn/dms/v2/home?region=cn-northwest-1#endpointList
选中source-db和target-db，在【操作】下拉菜单里选择"删除"选项。并在弹出窗口中点击【删除】按钮。
![](/images/CleanUp/deleteEndpoints.png)

2.删除Storage Gateway：

* 在xshell里，分别双击"local-idc-env"和"remote-aws-env"，从而进入本地数据中心的虚拟机以及AWS的容灾端的虚拟机里，执行下面的命令：
```bash
cd ~/
sudo umount /mnt
```

* 进入storage gateway的文件共享控制台：https://console.amazonaws.cn/storagegateway/home/file-shares?region=cn-north-1

选中文件共享，并在"操作"下拉菜单里选择"删除文件共享"。选中"勾选此框以确认删除以下资源"复选框，点击【删除】按钮。

* 进入storage gateway的网关控制台：https://console.amazonaws.cn/storagegateway/home/gateways?region=cn-north-1

选中名为"backup-filegw"的网关，在【操作】下拉菜单里选择"删除网关"选项。选中"勾选此框以确认删除以下资源"复选框，点击【删除】按钮。

* 进入EC2的控制台，找到Filegateway的EC2实例：https://console.amazonaws.cn/ec2/v2/home?region=cn-north-1#Instances:search=Filegateway;sort=launchTime

在【操作】下拉菜单里选择"实例状态"选项，并选择"终止"选项。并在弹出窗口中选择【是,请终止】按钮。
![](/images/CleanUp/deleteStorageGWEC2.png)

2.删除VPC对等连接：vpc-peering。进入北京region的VPC Peering控制台：https://console.amazonaws.cn/vpc/home?region=cn-north-1#PeeringConnections:sort=vpcPeeringConnectionId
选中VPC Peering，然后在【操作】下拉菜单里，选择"删除VPC对等连接"选项。
在弹出的窗口中，选择"删除相关路由表条目"复选框，然后点击【是,删除】按钮。
![](/images/CleanUp/deleteVPCPeering1.png)

3.在CloudEndure里，在Machines里，选中Wordpress APP，然后在Machime action里，选中"Remove 1 Machine From This Console"
![](/images/CleanUp/removeMachineFromCE.png)
在PROJECT ACTION里，选择"Delete Current Project"选项，删除wp-dr项目。

4.进入宁夏region的EC2控制台：https://cn-northwest-1.console.amazonaws.cn/ec2/v2/home?region=cn-northwest-1#Instances:tag:Name=CloudEndure,APP;sort=launchTime

选择界面上显示的两台EC2，然后在【操作】下拉菜单里，选择"实例状态"，以及"终止"选项，从而终止这两台EC2。

5.进入宁夏region的CloudFormation console：https://cn-northwest-1.console.amazonaws.cn/cloudformation/home?region=cn-northwest-1#/stacks?filteringText=&filteringStatus=active&viewNested=true&hideStacks=false
选中dr-site堆栈，并点击【删除】按钮。在弹出窗口中，点击【删除堆栈】按钮。
如果遇到错误，则进入VPC界面：https://cn-northwest-1.console.amazonaws.cn/vpc/home?region=cn-northwest-1#vpcs:sort=VpcId
选中名为"BCDRVPC"的VPC，然后点击【操作】菜单，在下拉列表里选择"Delete VPC"，并在弹出的窗口上点击【Delete VPC】
等VPC删除完毕以后，再次删除dr-site堆栈。

6.进入北京region的CloudFormation console：https://console.amazonaws.cn/cloudformation/home?region=cn-north-1#/stacks?filteringText=&filteringStatus=active&viewNested=true&hideStacks=false
选中local-idc-env堆栈，并点击【删除】按钮。在弹出窗口中，点击【删除堆栈】按钮。

7.删除名为"storagegateway-coldbackup-xxx"的S3 bucket。

8.删除Key Pair。进入Key Pair控制台：https://console.amazonaws.cn/ec2/v2/home?region=cn-north-1#KeyPairs:

选中"local-idc-key"，在【Actions】下拉菜单里，选择"Delete"选项，在弹出的窗口中，输入"delete"，并点击【Delete】按钮。

9.删除IAM用户：demouser。进入IAM user的控制台：https://console.amazonaws.cn/iam/home?region=cn-northwest-1#/users/demouser

点击【删除用户】按钮，并点击【是,删除】按钮。

