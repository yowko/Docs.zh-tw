---
title: "如何：在 Windows Form 上建立簡單繫結控制項 | Microsoft Docs"
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
  - "資料繫結, 簡單資料繫結"
  - "Windows Form 控制項, 資料繫結"
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：在 Windows Form 上建立簡單繫結控制項
您可以利用「*簡單繫結*」顯示控制項中的單一資料項目，例如資料集資料表中的資料行值。  您也可以將控制項的任何屬性簡單繫結至資料值。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要簡單繫結控制項  
  
1.  連接至資料來源。  如需詳細資訊，請參閱[連接資料來源](../../../docs/framework/data/adonet/connecting-to-a-data-source.md)。  
  
2.  請在表單中選取控制項，並且顯示 \[**屬性**\] 視窗。  
  
3.  展開 \[**\(DataBindings\)**\] 屬性。  
  
     最常被繫結的屬性會顯示在 \[**DataBindings**\] 屬性之下。  例如，在大多數的控制項中，\[**Text**\] 屬性是最常被繫結的。  
  
4.  如果您要繫結的屬性不是經常繫結的屬性之一，請按一下 \[**\(進階\)**\] 方塊中的 \[**省略**\] 按鈕 \(![VisualStudioEllipsesButton 螢幕擷取畫面](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\)，便可顯示 \[**格式化與進階繫結**\] 對話方塊以及該控制項之屬性的完整清單。  
  
5.  選取您要繫結的屬性，並按一下 \[**繫結**\] 之下的下拉箭號。  
  
     可用資料來源的清單隨即顯示。  
  
6.  展開您要繫結至的資料來源，直到找到所要的單一資料項目。  例如，如果要繫結至資料集資料表中的某資料行值，請展開該資料集的名稱，再展開資料表名稱以顯示資料行名稱。  
  
7.  按一下要繫結的項目名稱。  
  
8.  如果先前是在 \[**格式化與進階繫結**\] 對話方塊中作業，按一下 \[**確定**\]，便可回到 \[**屬性**\] 視窗。  
  
9. 如果想要繫結控制項的其他屬性，請重複步驟 3 至 7。  
  
    > [!NOTE]
    >  因為簡單繫結控制項只會顯示單一資料項目，所以巡覽邏輯會經常包含在具有簡單繫結控制項的 Windows Form 中。  
  
## 請參閱  
 <xref:System.Windows.Forms.Binding>   
 [Windows Form 資料繫結](../../../docs/framework/winforms/windows-forms-data-binding.md)   
 [資料繫結和 Windows Form](../../../docs/framework/winforms/data-binding-and-windows-forms.md)