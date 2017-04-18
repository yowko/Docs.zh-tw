---
title: "Windows Form 中的電源管理 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "電池狀態"
  - "電源狀態"
ms.assetid: ad04a801-5682-4d88-92c5-26eb9cdb209a
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Windows Form 中的電源管理
Windows Form 應用程式也可以使用 Windows 作業系統中的電源管理功能。  您可以透過應用程式監視電腦的電源狀態，並且在狀態發生變更時採取必要動作。  例如，如果應用程式是在攜帶型電腦上執行，當電腦的電池電力低於某種程度時，可能就需要停用應用程式中的某些功能。  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 提供了 <xref:Microsoft.Win32.SystemEvents.PowerModeChanged> 事件，每當電源狀態變更時就會發生此事件，例如，當使用者暫停或繼續執行作業系統時，或者當交流電源狀態或電池狀態變更時。  <xref:System.Windows.Forms.SystemInformation> 類別的 <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> 屬性可以用來查詢目前的狀態，如下列程式碼範例所示：  
  
 [!code-csharp[PowerMode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#1)]
 [!code-vb[PowerMode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#1)]  
  
 除了 <xref:System.Windows.Forms.BatteryChargeStatus> 列舉型別以外，<xref:System.Windows.Forms.SystemInformation.PowerStatus%2A> 屬性也包含列舉型別，可用來判斷電池容量 \(<xref:System.Windows.Forms.PowerStatus.BatteryFullLifetime%2A>\) 和電池的充電百分比 \(<xref:System.Windows.Forms.PowerStatus.BatteryLifePercent%2A>、<xref:System.Windows.Forms.PowerStatus.BatteryLifeRemaining%2A>\)。  
  
 您可以使用 <xref:System.Windows.Forms.Application> 的 <xref:System.Windows.Forms.Application.SetSuspendState%2A> 方法，使電腦進入休眠或暫停模式。  如果 `force` 引數是設定為 `false`，作業系統就會將事件傳送至要求暫止使用權限的所有應用程式。  如果 `disableWakeEvent` 引數是設定為 `true`，作業系統就會停用所有喚醒事件。  
  
 下列程式碼範例會示範如何使電腦進入休眠狀態。  
  
 [!code-csharp[PowerMode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/powermode/cs/form1.cs#2)]
 [!code-vb[PowerMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/powermode/vb/form1.vb#2)]  
  
## 請參閱  
 <xref:Microsoft.Win32.SystemEvents.PowerModeChanged>   
 <xref:System.Windows.Forms.SystemInformation.PowerStatus%2A>   
 <xref:System.Windows.Forms.Application.SetSuspendState%2A>   
 <xref:Microsoft.Win32.SystemEvents.SessionSwitch>