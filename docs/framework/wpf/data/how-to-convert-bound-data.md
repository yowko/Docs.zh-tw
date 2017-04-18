---
title: "如何：轉換繫結的資料 | Microsoft Docs"
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
  - "資料繫結, 轉換繫結資料"
  - "轉換, 繫結資料"
  - "資料繫結, 轉換繫結資料"
ms.assetid: b00aaa19-c6df-4c3b-a9fd-88a0b488df2b
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：轉換繫結的資料
這個範例顯示如何將轉換套用至繫結中使用的資料。  
  
 若要在繫結期間轉換資料，您必須建立實作 <xref:System.Windows.Data.IValueConverter> 介面的類別，這個介面包含 <xref:System.Windows.Data.IValueConverter.Convert%2A> 和 <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> 方法。  
  
## 範例  
 下列範例顯示日期轉換器的實作，它會將傳入的資料值轉換，使其僅顯示年、月和日的資訊。  在實作 <xref:System.Windows.Data.IValueConverter> 介面時，在實作中加入 <xref:System.Windows.Data.ValueConversionAttribute> 屬性 \(Attribute\) 以向開發工具指出轉換時牽涉到的資料型別，是個不錯的做法，如下列範例所示：  
  
 [!code-csharp[DataBindingLab#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DateConverter.cs#18)]
 [!code-vb[DataBindingLab#18](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/DateConverter.vb#18)]  
  
 轉換器建立完成後，就可以將它加入您的[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 檔案中做為資源。  在下列範例中，*src* 對應至的命名空間是定義 *DateConverter* 的命名空間。  
  
 [!code-xml[DataBindingLab#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#15)]  
  
 最後，您可以用下列語法在繫結中使用轉換器。  在下列範例中，<xref:System.Windows.Controls.TextBlock> 的文字內容已繫結至外部資料來源的 *StartDate* 屬性 \(Property\)。  
  
 [!code-xml[DataBindingLab#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/DataBindingLabApp.xaml#17)]  
  
 上述範例中參考的樣式資源是在資源區段中定義，但是不會在這個主題中顯示。  
  
## 請參閱  
 [實作繫結驗證](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)   
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)