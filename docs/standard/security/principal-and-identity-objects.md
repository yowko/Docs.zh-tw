---
title: "Principal and Identity Objects | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "WindowsIdentity objects"
  - "GenericIdentity objects"
  - "GenericPrincipal objects"
  - "identity objects, about identity objects"
  - "security [.NET Framework], identity objects"
  - "principal objects, about principal objects"
  - "security [.NET Framework], principals"
  - "WindowsPrincipal objects"
ms.assetid: aa5930ad-f3d7-40aa-b6f6-c6edcd5c64f7
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# Principal and Identity Objects
Managed 程式碼可以透過 [Principal](frlrfSystemSecurityPrincipalIPrincipalClassTopic) 物件 \(其包含對 [Identity](frlrfSystemSecurityPrincipalIIdentityClassTopic) 物件的參考\) 探索主體的識別或角色。  將 Identity 和 Principal 物件與像使用者和群組帳戶的類似概念相比較，可能很有幫助。  大部分的網路環境中，使用者帳戶代表人員或程式，而群組帳戶代表使用者的某些類別和他們擁有的權限。  同樣的，.NET Framework 的 Identity 物件代表使用者，而角色代表成員資格和安全性內容。  在 .NET Framework 中，Principal 物件會將 Identity 物件和角色兩者都封裝。.NET Framework 應用程式會根據它的識別或它的角色成員資格 \(更為常見\)，將權限授與主體。  
  
## Identity 物件  
 Identity 物件會封裝有關使用者或驗證過的實體 \(Entity\) 的資訊。  在它們最基本的層級上，Identity 物件包含名稱和驗證類型。  名稱可以是使用者名稱或 Windows 帳戶名稱兩者之一，而驗證類型則可為所支援的登入通訊協定 \(例如 Kerberos V5\) 或自訂值兩者之一。  .NET Framework 定義可用於大多數自訂登入案例的 <xref:System.Security.Principal.GenericIdentity> 物件，和更特殊的 <xref:System.Security.Principal.WindowsIdentity> 物件，其可使用在您想要應用程式仰賴 Windows 驗證時。  此外，您可以定義您自己的 Identity 類別以封裝自訂的使用者資訊。  
  
 <xref:System.Security.Principal.IIdentity> 介面定義存取名稱和驗證類型的屬性，例如 Kerberos V5 或 NTLM。  所有 **Identity** 類別實作 **IIdentity** 介面。  **Identity** 物件與 Windows NT 處理語彙基元 \(其下的執行緒目前正在執行\) 之間沒有必要的關係。  然而，如果 **Identity** 物件為 **WindowsIdentity** 物件，識別則假設為代表 Windows NT 安全性語彙基元。  
  
## Principal 物件  
 Principal 物件代表其下程式碼正在執行的安全性內容。  實作以角色為基礎安全性的應用程式會根據與 Principal 物件相關的角色來授與權限。  類似於 Identity 物件，.NET Framework 提供 <xref:System.Security.Principal.GenericPrincipal> 物件和 <xref:System.Security.Principal.WindowsPrincipal> 物件。  您也可以定義您自己的自訂主體類別。  
  
 <xref:System.Security.Principal.IPrincipal> 介面會定義屬性以存取關聯的**Identity** 物件，而且也會定義方法以判斷 **Principal** 物件所識別的使用者是否為指定角色的成員。  所有 **Principal** 類別實作 **IPrincipal** 介面，而且也實作任何必要的額外屬性和方法。  例如，Common Language Runtime 提供 **WindowsPrincipal** 類別，實作額外功能來將 Windows NT 或 Windows 2000 群組成員資格對應至角色。  
  
 **Principal** 物件是繫結至應用程式定義域 \(<xref:System.AppDomain>\) 內的呼叫內容 \(<xref:System.Runtime.Remoting.Messaging.CallContext>\) 物件。  預設的呼叫內容永遠與新的 **AppDomain** 一起建立，所以總是有呼叫內容可以用來接受 **Principal** 物件。  當新執行緒建立時，**CallContext** 物件也為執行緒而建立。  **Principal** 物件參考是自動從建立的執行緒複製到新執行緒的 **CallContext**。  如果執行階段不能判斷哪一個 **Principal** 物件屬於執行緒的建立者，則遵循建立 **Principal** 和 **Identity** 物件的預設原則。  
  
 可設定的應用程式定義域特定原則定義規則，來決定什麼類型的 **Principal** 物件與新應用程式定義域相關聯。  若是安全性原則許可，執行階段可以建立 **Principal** 和 **Identity** 物件，以反映與執行的目前執行緒相關聯的作業系統語彙基元。  預設的情況下，執行階段使用代表未驗證使用者的 **Principal** 和 **Identity** 物件。  執行階段不會建立這些預設 **Principal** 和 **Identity** 物件，直到程式碼嘗試存取它們。  
  
 建立應用程式定義域的信任程式碼可以設定控制預設 **Principal** 和 **Identity** 物件建構的應用程式定義域原則。  這個應用程式定義域特定原則可套用到應用程式定義域中所有的執行緒。  Unmanaged 且信任的主應用程式原本就有能力設定這個原則，但設定這個原則的 Managed 程式碼必須擁有控制定義域原則的 <xref:System.Security.Permissions.SecurityPermission?displayProperty=fullName>。  
  
 當 **Principal** 物件在應用程式定義域間傳輸，但於相同處理序內 \(即因而在相同電腦上\) 時，遠端基礎結構會複製參考至 **Principal** 物件，將呼叫端內容關聯到被呼叫端內容。  
  
## 請參閱  
 [How to: Create a WindowsPrincipal Object](../../../docs/standard/security/how-to-create-a-windowsprincipal-object.md)   
 [How to: Create GenericPrincipal and GenericIdentity Objects](../../../docs/standard/security/how-to-create-genericprincipal-and-genericidentity-objects.md)   
 [Replacing a Principal Object](../../../docs/standard/security/replacing-a-principal-object.md)   
 [Impersonating and Reverting](../../../docs/standard/security/impersonating-and-reverting.md)   
 [Role\-Based Security](../../../docs/standard/security/role-based-security.md)   
 [Key Security Concepts](../../../docs/standard/security/key-security-concepts.md)