---
title: "Windows Form 安全性 | Microsoft Docs"
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
  - "存取控制, Windows Form"
  - "設計工具存取安全性"
  - "權限, Windows Form"
  - "安全性 [Windows Form]"
  - "安全性原則, Windows Form"
  - "Windows Form, 安全性"
ms.assetid: 932d438a-5285-46d8-a958-8c93d0ad6cae
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Windows Form 安全性
Windows Form 的特色在於以程式碼為基底的安全性模型 \(也就是說，無論使用者是否執行程式碼，安全性層級都是針對程式碼設定的\)。  這是用來加強電腦系統上已有的任何安全性結構描述 \(Schema\)。  這些可包括瀏覽器的結構描述 \(例如 Internet Explorer 中可使用的以地區為基礎的安全性\) 或作業系統的結構描述 \(例如 Windows NT 的以認證為基礎的安全性\)。  
  
## 在本節中  
 [Windows Form 中的安全性概觀](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 簡單說明 .NET Framework 安全性模型，以及確保應用程式中 Windows Form 安全性的必要基本步驟。  
  
 [Windows Form 中更安全的檔案和資料存取](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 描述如何在非完全信任的環境中存取檔案和資料。  
  
 [Windows Form 中更安全的列印](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)  
 描述如何在非完全信任的環境中存取列印功能。  
  
 [Windows Form 中的其他安全性考量](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 說明在非完全信任的環境中，執行視窗操作 \(Manipulation\)、使用 \[剪貼簿\] 和呼叫 Unmanaged 程式碼。  
  
## 相關章節  
 [NIB: Default Security Policy](http://msdn.microsoft.com/zh-tw/2c086873-0894-4f4d-8f7e-47427c1a3b55)  
 列出完全信任、近端內部網路和網際網路使用權限集合中授與的預設使用權限。  
  
 [NIB: General Security Policy Administration](http://msdn.microsoft.com/zh-tw/5121fe35-f0e3-402c-94ab-4f35b0a87b4b)  
 提供關於管理 .NET Framework 安全性原則和提高使用權限的資訊。  
  
 [Dangerous Permissions and Policy Administration](../../../docs/framework/misc/dangerous-permissions-and-policy-administration.md)  
 討論有些可能讓安全性系統受到傷害的 .NET Framework 使用權限。  
  
 [Secure Coding Guidelines](../../../docs/standard/security/secure-coding-guidelines.md)  
 說明針對 .NET Framework 安全撰寫程式碼之最佳實例的主題連結。  
  
 [NIB: Requesting Permissions](http://msdn.microsoft.com/zh-tw/0447c49d-8cba-45e4-862c-ff0b59bebdc2)  
 討論屬性的使用，讓 Runtime 知道程式碼執行時需要何種使用權限。  
  
 [Key Security Concepts](../../../docs/standard/security/key-security-concepts.md)  
 涵蓋程式碼安全性基本層面的主題連結。  
  
 [Code Access Security Basics](../../../docs/framework/misc/code-access-security-basics.md)  
 討論使用 .NET Framework Run Time 安全性原則的基本概念。  
  
 [NIB: Determining When to Modify Security Policy](http://msdn.microsoft.com/zh-tw/af749b17-e461-409d-84b9-a3d44789db16)  
 說明如何判斷您的應用程式何時需要偏離預設安全性原則。  
  
 [NIB: Deploying Security Policy](http://msdn.microsoft.com/zh-tw/f936c1e5-033b-4bd9-a3bd-a39ba733a681)  
 討論部署安全性原則變更的最佳方式。