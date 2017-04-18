---
title: "如何：建立含陰影的文字 | Microsoft Docs"
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
  - "文字中的陰影效果"
  - "文字, 已遮蔽"
  - "印刷樣式, 陰影效果"
ms.assetid: 6ab9c754-6001-4708-b479-5367f2fd1a35
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 如何：建立含陰影的文字
本節範例顯示如何建立所顯示文字的陰影效果。  
  
## 範例  
 <xref:System.Windows.Media.Effects.DropShadowEffect> 物件可讓您建立 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 物件的各種下拉式陰影效果。  下列範例顯示套用至文字的下拉式陰影效果。  在這種情況下，陰影是柔和陰影，表示陰影色彩模糊。  
  
 ![Softness &#61; 0.25 的文字陰影](../../../../docs/framework/wpf/advanced/media/shadowtext01.png "ShadowText01")  
含柔和陰影的文字範例  
  
 設定 <xref:System.Windows.Media.Effects.DropShadowEffect.ShadowDepth%2A> 屬性，就可以控制陰影的寬度。  值 `4.0` 表示陰影寬度是 4 個像素。  而修改 <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> 屬性，則可以控制陰影的柔和度或模糊。  值 `0.0` 表示沒有模糊。  下列程式碼範例顯示如何建立柔和陰影。  
  
 [!code-xml[TextShadowSnippets#TextShadowSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet1)]  
  
> [!NOTE]
>  這些陰影效果並不會使用 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 文字呈現管線。  因此，在使用這些效果時會停用 ClearType。  
  
 下列範例顯示套用至文字的強烈下拉式陰影效果。  在這種情況下，陰影不會模糊。  
  
 ![Softness &#61; 0 的文字陰影](../../../../docs/framework/wpf/advanced/media/shadowtext02.png "ShadowText02")  
含強烈陰影的文字範例  
  
 將 <xref:System.Windows.Media.Effects.DropShadowEffect.BlurRadius%2A> 屬性設定為 `0.0` \(表示未使用任何模糊\)，就可以建立強烈陰影。  而修改 <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> 屬性，則可以控制陰影的方向。  請將這個屬性的方向值設定為介於 `0` 與 `360` 之間的度數。  下圖顯示 <xref:System.Windows.Media.Effects.DropShadowEffect.Direction%2A> 屬性設定的方向值。  
  
 ![陰影的 DropShadow 程度設定](../../../../docs/framework/wpf/advanced/media/shadowtext08.png "ShadowText08")  
DropShadow 方向圖表  
  
 下列程式碼範例顯示如何建立強烈陰影。  
  
 [!code-xml[TextShadowSnippets#TextShadowSnippet2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/SingleShadows.xaml#textshadowsnippet2)]  
  
## 使用模糊效果  
 <xref:System.Windows.Media.Effects.BlurBitmapEffect> 可以用來建立放在文字物件後面的類似陰影效果。  套用至文字的模糊點陣圖效果會均勻地模糊所有方向。  
  
 下列範例顯示套用至文字的模糊效果。  
  
 ![使用 BlurBitmapEffect 的文字陰影](../../../../docs/framework/wpf/advanced/media/shadowtext06.png "ShadowText06")  
具有模糊效果的文字範例  
  
 下列程式碼範例顯示如何建立模糊效果。  
  
 [!code-xml[TextShadowSnippets#TextShadowSnippet6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/BlurShadows.xaml#textshadowsnippet6)]  
  
## 使用 Translate 轉換  
 <xref:System.Windows.Media.TranslateTransform> 可以用來建立放在文字物件後面的類似陰影效果。  
  
 下列程式碼範例會使用 <xref:System.Windows.Media.TranslateTransform> 使文字產生位移。  在這個範例中，主要文字略為下方的位置有段完全相同的文字，以產生陰影效果。  
  
 ![使用 TranslateTransform 的文字陰影](../../../../docs/framework/wpf/advanced/media/shadowtext07.png "ShadowText07")  
使用轉換產生陰影效果之文字的範例  
  
 下列程式碼範例顯示如何建立轉換以取得陰影效果。  
  
 [!code-xml[TextShadowSnippets#TextShadowSnippet7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextShadowSnippets/CS/TransformShadows.xaml#textshadowsnippet7)]