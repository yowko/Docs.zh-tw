---
title: "Creating a Cryptographic Scheme | Microsoft Docs"
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
  - "encryption [.NET Framework], creating cryptographic schemes"
  - "cryptography [.NET Framework], creating cryptographic schemes"
ms.assetid: d40c509f-5a5e-46cc-94cb-a951e9ab6843
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# Creating a Cryptographic Scheme
.NET Framework 的密碼編譯元件可以結合以建立不同的配置，來加密和解密資料。  
  
 加密和解密資料的簡單密碼編譯配置可能會指定下列步驟：  
  
1.  每一方產生一個公開\/私密金鑰組。  
  
2.  各方交換他們的公開金鑰。  
  
3.  比方說，每一方產生 TripleDES 加密的祕密金鑰，並對方的公開金鑰加密新建立的金鑰。  
  
4.  每一方傳送資料至對方，並依特定順序合併對方的秘密金鑰與自己的秘密金鑰，建立新的秘密金鑰。  
  
5.  接著各方使用對稱加密開始交談。  
  
 建立密碼編譯配置不是簡單的工作。  如需有關使用密碼編譯的詳細資訊，請參閱 http:\/\/msdn.microsoft.com\/library 的平台 SDK 文件中的＜密碼編譯＞主題。  
  
## 請參閱  
 [密碼編譯服務](../../../docs/standard/security/cryptographic-services.md)