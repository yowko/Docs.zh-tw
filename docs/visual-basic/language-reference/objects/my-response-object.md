---
title: "My.Response Object | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "My.MyWebExtension.Response"
  - "My.Response"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Response object"
ms.assetid: 626359bc-3165-40b4-bfaf-2c610e26eb5b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# My.Response Object
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

取得與 <xref:System.Web.UI.Page> 相關聯的 <xref:System.Web.HttpResponse> 物件。  這個物件允許您傳送 HTTP 回應資料給用戶端，並包含該回應的資訊。  
  
## 備註  
 `My.Response` 物件包含目前與頁面相關聯的 <xref:System.Web.HttpResponse> 物件。  
  
 `My.Response` 物件只能用於 [!INCLUDE[vstecasp](../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)] 應用程式。  
  
## 範例  
 下列範例會取得 `My.Request` 物件的標頭集合，並使用 `My.Response` 物件將該集合寫入 ASP.NET 網頁。  
  
 [!code-vb[VbVbalrMyWeb#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-response-object_1.aspx)]  
  
## 請參閱  
 <xref:System.Web.HttpResponse>   
 [My.Request Object](../../../visual-basic/language-reference/objects/my-request-object.md)