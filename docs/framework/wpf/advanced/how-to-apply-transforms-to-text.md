---
title: "如何：對文字套用轉換 | Microsoft Docs"
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
  - "旋轉文字"
  - "縮放文字"
  - "陰影文字"
  - "傾斜文字"
  - "文字的轉換"
  - "轉譯文字"
  - "印刷樣式, 旋轉文字"
  - "印刷樣式, 縮放文字"
  - "印刷樣式, 陰影文字"
  - "印刷樣式, 傾斜文字"
  - "印刷樣式, 轉換"
  - "印刷樣式, 轉譯文字"
ms.assetid: 0d61678a-4185-4f2a-85c6-c1d020f96fa0
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 如何：對文字套用轉換
轉換可改變您的應用程式中所顯示的文字。  下列範例使用不同類型的呈現轉換來影響 <xref:System.Windows.Controls.TextBlock> 控制項中的文字顯示。  
  
## 範例  
 下列範例顯示使文字在二維 x\-y 平面中繞著所指定點旋轉的情形。  
  
 ![使用 RotateTransform 旋轉的文字](../../../../docs/framework/wpf/advanced/media/transformedtext01.png "TransformedText01")  
文字旋轉 90 度的範例  
  
 下列程式碼範例會使用 <xref:System.Windows.Media.RotateTransform> 旋轉文字。  90 <xref:System.Windows.Media.RotateTransform.Angle%2A> 這個值會使項目以順時針方向旋轉 90 度。  
  
 [!code-xml[TextTransformSample#TextTransformSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 下列範例顯示第二行文字沿著 X 軸調整 150%，第三行文字沿著 Y 軸調整 150%。  
  
 ![使用 ScaleTransform 縮放的文字](../../../../docs/framework/wpf/advanced/media/transformedtext02.png "TransformedText02")  
縮放文字範例  
  
 下列程式碼範例會使用 <xref:System.Windows.Media.ScaleTransform> 使文字脫離原始大小。  
  
 [!code-xml[TextTransformSample#TextTransformSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
>  縮放文字與增加文字的字型大小不同。  字型大小會個別獨立計算，以便在不同大小中提供最理想的解析度。  縮放文字會保留原始文字大小的比例。  
  
 下列範例顯示文字沿著 X 軸傾斜。  
  
 ![使用 SkewTransform 傾斜的文字](../../../../docs/framework/wpf/advanced/media/transformedtext03.png "TransformedText03")  
傾斜文字的範例  
  
 下列程式碼範例會使用 <xref:System.Windows.Media.SkewTransform> 傾斜文字。  傾斜也稱為切變，這種轉換會以非一致的方式延伸座標空間。  在這個範例中，有兩個文字字串會分別沿著 x 座標傾斜 \-30° 和 30°。  
  
 [!code-xml[TextTransformSample#TextTransformSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 下列範例顯示沿著 x 與 y 軸平移或移動的文字。  
  
 ![使用 TranslateTransform 的文字位移](../../../../docs/framework/wpf/advanced/media/transformedtext04.png "TransformedText04")  
平移文字的範例  
  
 下列程式碼範例會使用 <xref:System.Windows.Media.TranslateTransform> 使文字產生位移。  在這個範例中，主要文字略為下方的位置有段完全相同的文字，以產生陰影效果。  
  
 [!code-xml[TextTransformSample#TextTransformSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
>  <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> 提供了一組豐富而可產生陰影效果的功能。  如需詳細資訊，請參閱 [建立含陰影的文字](../../../../docs/framework/wpf/advanced/how-to-create-text-with-a-shadow.md)。  
  
## 請參閱  
 [對文字套用動畫](../../../../docs/framework/wpf/advanced/how-to-apply-animations-to-text.md)