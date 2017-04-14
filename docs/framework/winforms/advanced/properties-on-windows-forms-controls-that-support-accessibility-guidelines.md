---
title: "支援可及性方針的 Windows Form 控制項屬性 | Microsoft Docs"
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
  - "網頁可及性, Windows Form 控制項屬性"
  - "Windows Form, 控制項的可及性屬性"
ms.assetid: ad3567a6-313b-4708-9e15-f487a831f049
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 支援可及性方針的 Windows Form 控制項屬性
Windows Form 標準工具箱上的控制項，支援大多數的可及性方針，包含顯露鍵盤焦點和顯露螢幕項目。  
  
## 事先規劃可及性  
 控制項的屬性 \(Property\) 可用於支援其他可及性方針，如下表所示。  此外，您應使用功能表提供程式功能的存取。  
  
|控制項屬性|可及性考量|  
|-----------|-----------|  
|AccessibleDescription|說明會回報至協助工具輔助，例如螢幕助讀員。  協助工具輔助是特定程式和裝置，可以協助殘障人士更有效率地使用電腦。|  
|AccessibleName|會回報至協助工具輔助的名稱。|  
|AccessibleRole|描述使用者介面中的項目用法。|  
|TabIndex|在表單中建立直覺式巡覽路徑。  讓沒有內建標記的控制項 \(例如文字方塊\) 能夠將相關標記依定位順序緊接著置於前面，是非常重要的考量。|  
|文字|使用 "&" 元建立便捷鍵 \(Access Key\)。  使用便捷鍵是提存取具備說明的功能鍵盤之一部分。|  
|字型大小|若字型大小無法調整，則應設定為 10 或更大的點數。  表單字型大小一旦設定，之後所有加入表單的控制項將會有相同的大小。|  
|Forecolor|若將此屬性設為預設值，則使用者的色彩設定將會用於表單上。|  
|Backcolor|若將此屬性設為預設值，則使用者的色彩設定將會用於表單上。|  
|BackgroundImage|讓此屬性 \(Property\) 保持空白，使文字更容易閱讀。|  
  
## 請參閱  
 [逐步解說：建立 Windows 架構的可及性應用程式](../../../../docs/framework/winforms/advanced/walkthrough-creating-an-accessible-windows-based-application.md)