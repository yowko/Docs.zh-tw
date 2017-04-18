---
title: "儲存筆墨 | Microsoft Docs"
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
  - "筆墨序列化格式 (ISF)"
  - "筆墨, 儲存"
  - "ISF (筆墨序列化格式)"
  - "擷取筆墨"
  - "儲存筆墨"
ms.assetid: a3f6d16b-d682-4680-9965-907332b4d2b8
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 儲存筆墨
<xref:System.Windows.Ink.StrokeCollection.Save%2A> 方法支援將筆墨儲存成筆墨序列化格式 \(Ink Serialized Format，ISF\)。  <xref:System.Windows.Ink.StrokeCollection> 類別的建構函式支援讀取筆墨資料。  
  
## 筆墨儲存和擷取  
 本節討論如何在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 平台中儲存和擷取筆墨。  
  
 下列範例會實作按鈕動作事件處理常式，會向使用者顯示 \[儲存檔案\] 對話方塊並將 <xref:System.Windows.Controls.InkCanvas> 中的筆墨儲存至檔案。  
  
 [!code-csharp[DigitalInkTopics#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#12)]
 [!code-vb[DigitalInkTopics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#12)]  
  
 下列範例會實作按鈕動作事件處理常式，會向使用者顯示 \[開啟檔案\] 對話方塊並從檔案將筆墨讀取至 <xref:System.Windows.Controls.InkCanvas> 項目中。  
  
 [!code-csharp[DigitalInkTopics#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#13)]
 [!code-vb[DigitalInkTopics#13](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#13)]  
  
## 請參閱  
 <xref:System.Windows.Controls.InkCanvas>   
 [Windows Presentation Foundation](../../../../docs/framework/wpf/index.md)