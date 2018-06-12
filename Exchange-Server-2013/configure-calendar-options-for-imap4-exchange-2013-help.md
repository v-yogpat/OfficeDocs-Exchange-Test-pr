﻿---
title: 'Configure calendar options for IMAP4: Exchange 2013 Help'
TOCTitle: Configure calendar options for IMAP4
ms:assetid: 6679c8b2-3f0f-449a-a17c-a7b30001538c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Aa998606(v=EXCHG.150)
ms:contentKeyID: 50395400
ms.date: 12/09/2016
mtps_version: v=EXCHG.150
---

# Configure calendar options for IMAP4

 

_**Applies to:** Exchange Server 2013_


You can use the Shell to configure calendaring access settings for your users who connect to their mailboxes using IMAP4 connections. The settings you specify determine how your IMAP4 users can access their calendar and exchange calendar information (for example, send or respond to a meeting request) with other users.

For additional information related to IMAP4, see [POP3 and IMAP4 in Exchange Server 2013](pop3-and-imap4-in-exchange-server-2013-exchange-2013-help.md).

## What do you need to know before you begin?

  - Estimated time to complete: 5 minutes.

  - You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "IMAP4 settings" entry in the [Clients and mobile devices permissions](clients-and-mobile-devices-permissions-exchange-2013-help.md) topic.

  - For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).


> [!TIP]
> Having problems? Ask for help in the Exchange forums. Visit the forums at <A href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</A>, <A href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</A>, or <A href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</A>..



## Use the Shell to set the calendar options for IMAP4

This example enables IMAP4 users to use the iCalendar standard, a standard for exchanging calendar information.

    Set-ImapSettings -Identity CAS01 -CalendarItemRetrievalOption iCalendar

This example enables IMAP4 users to access calendar information from an internal server.

    Set-ImapSettings -Identity CAS01 -CalendarItemRetrievalOption IntranetUrl 

This example enables IMAP4 users to access calendar information from the Internet on an external server.

    Set-ImapSettings -CalendarItemRetrievalOption InternetUrl

This example enables IMAP4 users to access calendar information by using a direct Outlook Web App URL. If you’re using `Custom`, you must specify an Outlook Web App URL using the *OWAServerUrl* parameter.

    Set-Imap4Settings -CalendarItemRetrievalOption Custom -OwaServerUrl "https://OwaServer01"

After you've specified the calendar options for IMAP4, you must restart the IMAP4 services. For information about how to restart the IMAP4 services, see [Start and stop the IMAP4 services](start-and-stop-the-imap4-services-exchange-2013-help.md).

For more information about syntax and parameters, see [Set-ImapSettings](https://technet.microsoft.com/en-us/library/aa998252\(v=exchg.150\)).

## How do you know this worked?

To verify that you’ve successfully set calendar options, do the following:

Run the following command in the Shell.

    Get-ImapSettings | format-list

Verify that the calendar settings are correct.

## For more information

After you set the calendar options for IMAP4, you may also want to:

[Configure POP3 and IMAP4 message retrieval format options](configure-pop3-and-imap4-message-retrieval-format-options-exchange-2013-help.md)

[Set connection time-out limits for IMAP4](set-connection-time-out-limits-for-imap4-exchange-2013-help.md)
