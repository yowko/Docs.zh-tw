---
title: "自訂權杖 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "安全性 [WCF], 自訂權杖"
ms.assetid: 8b2dbe29-dec2-4652-8e34-fb21bc1437b5
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 自訂權杖
儘管 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 原本就支援將 X.509 憑證、安全性內容權杖、Kerberos 票證，以及使用者名稱權杖當做認證來使用，但是這樣的彈性已經足夠讓您使用自己自訂的認證。  
  
## 在本節中  
 [HOW TO：建立自訂權杖](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)  
 說明如何使用 <xref:System.IdentityModel.Tokens.SecurityToken> 類別來建立自訂安全性權杖，以及如何將它與自訂安全性權杖提供者和驗證器整合。