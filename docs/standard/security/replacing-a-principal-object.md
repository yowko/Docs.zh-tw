---
title: "Replacing a Principal Object | Microsoft Docs"
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
  - "principal objects, replacing"
  - "security [.NET Framework], replacing principal objects"
  - "security [.NET Framework], principals"
ms.assetid: c323687e-b196-487b-beba-f38f9b3f961b
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# Replacing a Principal Object
提供驗證服務的應用程式必須能夠針對指定的執行緒取代**主體**物件 \(<xref:System.Security.Principal.IPrincipal>\)。 此外，因為惡意的附加檔案、不正確的**主體**會宣告為不實身分識別或角色，進而危及應用程式的安全性，所以安全性系統必須協助保護取代**主體**物件的能力。 因此，需要能夠取代**主體**物件的應用程式必須為其授與主體控制的 <xref:System.Security.Permissions.SecurityPermission?displayProperty=fullName> 物件。 \(請注意執行以角色為基礎的安全性檢查或建立**主體**物件並不需要此權限。\)  
  
 目前可以執行下列工作來取代**主體**物件：  
  
1.  建立取代**主體**物件和相關聯的**身分識別**物件。  
  
2.  將新的**主體**物件附加至呼叫內容。  
  
## 範例  
 下列範例示範如何建立一般的主體物件，並用來設定執行緒主體。  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## 請參閱  
 <xref:System.Security.Permissions.SecurityPermission?displayProperty=fullName>   
 [Principal and Identity Objects](../../../docs/standard/security/principal-and-identity-objects.md)