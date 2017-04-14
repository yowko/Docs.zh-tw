---
title: "如何：手動管理已緩衝的圖形 | Microsoft Docs"
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
  - "BufferedGraphicsContext 類別"
  - "重繪閃動, 手動管理圖形以減少"
  - "圖形, 管理緩衝的"
ms.assetid: 4c2a90ee-bbbe-4ff6-9170-1b06c195c918
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：手動管理已緩衝的圖形
如果是比較進階的雙重緩衝狀況，您可以使用 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 類別實作自己的雙重緩衝邏輯。  負責配置及管理個別圖形緩衝區的類別是 <xref:System.Drawing.BufferedGraphicsContext> 類別。  每一個應用程式都有自己的預設 <xref:System.Drawing.BufferedGraphicsContext>，以管理該應用程式所有的預設雙重緩衝。  您可以呼叫 <xref:System.Drawing.BufferedGraphicsManager.Current%2A>，藉此擷取這個執行個體的參考。  
  
### 若要取得預設 BufferedGraphicsContext 的參考  
  
-   設定 <xref:System.Drawing.BufferedGraphicsManager.Current%2A> 屬性，如下列程式碼範例所示：  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    >  您不需要呼叫 <xref:System.Drawing.BufferedGraphicsContext> 參考 \(接收自 <xref:System.Drawing.BufferedGraphicsManager> 類別\) 上的 `Dispose` 方法。  <xref:System.Drawing.BufferedGraphicsManager> 會處理預設的 <xref:System.Drawing.BufferedGraphicsContext> 執行個體所有的記憶體配置與散發。  
  
     如果是圖形密集的應用程式 \(例如動畫\)，有時候您也可以使用專屬的 <xref:System.Drawing.BufferedGraphicsContext> 以提高效能，而不使用由 <xref:System.Drawing.BufferedGraphicsManager> 所提供的 <xref:System.Drawing.BufferedGraphicsContext>。  這樣可讓您以個別的方式建立及管理圖形緩衝區，而不會因管理和應用程式相關聯的所有其他已緩衝圖形而增加效能負荷。  
  
### 若要建立專屬的 BufferedGraphicsContext  
  
-   宣告及建立 <xref:System.Drawing.BufferedGraphicsContext> 類別的新執行個體，如下列程式碼範例所示：  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## 請參閱  
 <xref:System.Drawing.BufferedGraphicsContext>   
 [雙重緩衝的圖形](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)   
 [如何：手動呈現已緩衝的圖形](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)