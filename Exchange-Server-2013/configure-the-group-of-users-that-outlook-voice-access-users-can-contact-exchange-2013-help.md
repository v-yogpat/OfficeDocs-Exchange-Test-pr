﻿---
title: 'Configure the group of users that Outlook Voice Access users can contact: Exchange 2013 Help'
TOCTitle: Configure the group of users that Outlook Voice Access users can contact
ms:assetid: a8dc0f9e-dc86-4128-af63-d4e550aed5bb
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Ee423551(v=EXCHG.150)
ms:contentKeyID: 49315486
ms.date: 12/10/2017
mtps_version: v=EXCHG.150
---

# Configure the group of users that Outlook Voice Access users can contact

 

_**Applies to:** Exchange Online, Exchange Server 2013, Exchange Server 2016_


You can specify which users can receive transferred calls or voice mail messages from Outlook Voice Access users. By default, the **In this dial plan only** option is selected. You can change this setting to allow Outlook Voice Access users to transfer calls or send voice messages to users located in the entire organization, to an existing UM auto attendant, or to a specific extension number.

For additional tasks related to UM dial plans, see [UM dial plan procedures](um-dial-plan-procedures-exchange-2013-help.md).

## What do you need to know before you begin?

  - Estimated time to complete: Less than 1 minute.

  - You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "UM dial plans" entry in the [Unified Messaging permissions](unified-messaging-permissions-exchange-2013-help.md) topic.

  - Before you perform these procedures, confirm that a UM dial plan has been created. For detailed steps, see [Create a UM dial plan](create-a-um-dial-plan-exchange-2013-help.md).

  - For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A>, or <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## What do you want to do?

## Use the EAC to configure the group of users that Outlook Voice Access users can contact

1.  In the EAC, navigate to **Unified Messaging** \> **UM dial plans**.

2.  In the list view, select the UM dial plan you want to modify, and then click **Edit** ![Edit icon](images/JJ218640.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Edit icon").

3.  On the **UM dial plan** page, click **Configure**.

4.  In **Transfer & search**, under **Allow callers to search for users by name or alias**, select one of the following options:
    
      - **In this dial plan only**   Use this option to allow Outlook Voice Access users who call in to an Outlook Voice Access number to locate and contact users who are within the same dial plan.
    
      - **In the entire organization**   Use this option to allow Outlook Voice Access users who call in to an Outlook Voice Access number to locate and contact anyone in the entire organization. This includes all users who are mailbox-enabled.
    
      - **Only on this auto attendant**   Use this option to allow Outlook Voice Access users who call in to an Outlook Voice Access number to connect to a specific auto attendant. You must create the auto attendant before you specify it here. This allows Outlook Voice Access users to be transferred to another auto attendant. The auto attendant you choose here can be a speech-enabled or non-speech-enabled auto attendant.
    
      - **Only for this extension**   Use this option to allow Outlook Voice Access users to connect to an extension number that you specify. You can use only numeric digits for the extension. The number of digits that you define in this field must match the number of digits in the extension numbers that are configured on the UM dial plan.

5.  Click **Save**.

## Use the Shell to configure the group of users that Outlook Voice Access users can contact

This example sets the group of users that Outlook Voice Access users can contact for a UM dial plan named `MyUMDialPlan` to the entire organization.

    Set-UMDialPlan -Identity MyUMDialPlan -ContactScope 'GlobalAddressList' -UMAutoAttendant $null -AllowDialPlanSubscribers $false -AllowExtensions $false

This example sets the group of users that Outlook Voice Access users can contact for a UM dial plan named `MyUMDialPlan` to the `DialPlan`.

    Set-UMDialPlan -Identity MyUMDialPlan -ContactScope DialPlan -AllowDialPlanSubscribers $false -AllowExtensions $false
