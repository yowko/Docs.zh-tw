---
title: "如何：在 XAML 中使用特殊字元 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "字元, 特殊"
  - "特殊字元"
  - "印刷樣式, 特殊字元"
  - "Unicode UTF-8 檔案格式"
  - "UTF-8 檔案格式"
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 3
---
# 如何：在 XAML 中使用特殊字元
在 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] 中建立的標記檔案會自動儲存成 [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF\-8 檔案格式，而這表示大部分的特殊字元都會正確編碼。  不過，有一組常用的特殊字元則採用不同的處理方式。  這些特殊字元遵照的是[!INCLUDE[TLA#tla_w3c](../../../../includes/tlasharptla-w3c-md.md)] [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] 的編碼標準。  
  
 下表顯示這組特殊字元的編碼語法。  
  
|字元|語法|描述|  
|--------|--------|--------|  
|\<|`<`|小於符號。|  
|\>|`>`|大於符號。|  
|&|`&`|連字號。|  
|「|`"`|雙引號。|  
  
> [!NOTE]
>  如果您使用文字編輯器 \(例如 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] 記事本\) 建立標記檔案，您必須將檔案儲存成 [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] UTF\-8 檔案格式，才能保留任何已編碼的特殊字元。  
  
 下列範例顯示如何在建立標記時在文字中使用特殊字元。  
  
## 範例  
 [!code-xml[SpecialCharsSnippets#SpecialCharsSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]