---
title: "GDI+ 中的中繼檔 | Microsoft Docs"
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
  - "GDI+, 中繼檔"
  - "影像 [Windows Form], 中繼檔"
  - "中繼檔"
ms.assetid: 51da872c-c783-440f-8bf6-1e580a966c31
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# GDI+ 中的中繼檔
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供 <xref:System.Drawing.Imaging.Metafile> 類別來記錄和顯示中繼檔。  中繼檔又稱為向量檔案，它是一種被儲存為繪圖命令和設定序列的影像。  <xref:System.Drawing.Imaging.Metafile> 物件中所記錄的命令和設定可儲存於記憶體或儲存至檔案或資料流。  
  
## 中繼檔的格式  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 可顯示儲存為下列格式的中繼檔：  
  
-   Windows 中繼檔 \(WMF\)  
  
-   加強型中繼檔 \(EMF\)  
  
-   EMF\+  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 可記錄 EMF 和 EMF\+ 格式的中繼檔，但無法記錄 WMF 格式的中繼檔。  
  
 EMF\+ 是 EMF 的擴充功能，可用來儲存 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 資料錄。  EMF\+ 格式有兩種變化：EMF\+ Only 和 EMF\+ Dual。  EMF\+ Only 中繼檔僅包含 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 資料錄。  此類中繼檔可由 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 顯示，但無法使用 [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] 顯示。  EMF\+ Dual 中繼檔包含 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 及 [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] 資料錄。  EMF\+ Dual 中繼檔的每個 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 資料錄都會與替代 [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] 資料錄配對。  此類中繼檔可由 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 或 [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] 顯示。  
  
 下列範例顯示先前儲存為檔案的中繼檔。  中繼檔的左上角顯示為 \(100, 100\)。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## 請參閱  
 [影像、點陣圖和中繼檔](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)