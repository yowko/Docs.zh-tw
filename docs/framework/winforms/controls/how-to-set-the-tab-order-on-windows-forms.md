---
title: "如何：在 Windows Form 上設定定位順序 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TabStop"
  - "TabIndex"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "控制項 [Windows Form], 設定定位順序"
  - "定位順序, Windows Form 上的控制項"
  - "Windows Form 控制項, 設定定位順序"
  - "Windows Form, 設定定位順序"
ms.assetid: 71fa8e76-0472-414b-ad3c-0f90166e0ad7
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 如何：在 Windows Form 上設定定位順序
定位順序是使用者藉著按 TAB 鍵，將焦點 \(Focus\) 從一個控制項移動到另一個控制項的順序。  每一個表單都有它自己的定位順序。  依照預設值，定位順序和您建立控制項的順序一樣。  定位順序從零開始計數。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要設定控制項的定位順序  
  
1.  選擇 \[**檢視**\] 功能表上的 \[**定位順序**\]。  
  
     這樣做會啟動表單上的定位順序選取模式。  每一控制項的左上角會出現一個數字 \(代表 <xref:System.Windows.Forms.Control.TabIndex%2A> 屬性\)。  
  
2.  循序按控制項以建立您要的定位順序。  
  
    > [!NOTE]
    >  控制項在定位順序中的位置可以設定成任何大於或等於 0 的數值。  若兩個控制項的數值重複，則以疊置順序為準，位於較頂端的控制項其定位順序排在前面。  \(疊置順序是沿著表單 Z 軸 \(深度\) 為表單控制項進行視覺分層。  疊置順序決定哪些控制項排在其他控制項的前面\)。 如需疊置順序的詳細資訊，請參閱[將 Windows Form 上的物件分層](../../../../docs/framework/winforms/controls/how-to-layer-objects-on-windows-forms.md)。  
  
3.  完成後，請再選擇 \[**檢視**\] 功能表上的 \[**定位順序**\]，離開定位順序模式。  
  
    > [!NOTE]
    >  不能夠得到焦點 \(Focus\) 的控制項，跟停用和不可見的控制項一樣，都沒有 <xref:System.Windows.Forms.Control.TabIndex%2A> 屬性，而且不包含在定位順序之中。  當使用者按 TAB 鍵，這些控制項會被略過。  
  
 另外，也可在 \[屬性\] 視窗中使用 <xref:System.Windows.Forms.Control.TabIndex%2A> 屬性設定定位順序。  控制項的 <xref:System.Windows.Forms.Control.TabIndex%2A> 屬性會決定它在定位順序中放置的位置。  根據預設，第一個加入的控制項的 <xref:System.Windows.Forms.Control.TabIndex%2A> 值為 0，第二個控制項的 <xref:System.Windows.Forms.Control.TabIndex%2A> 值為 1，以此類推。  
  
 此外，根據預設，<xref:System.Windows.Forms.GroupBox> 控制項有自己的 <xref:System.Windows.Forms.Control.TabIndex%2A> 值，而這個值是整數。  <xref:System.Windows.Forms.GroupBox> 控制項本身在執行階段不能取得焦點。  於是，<xref:System.Windows.Forms.GroupBox> 內的每一個控制項都有自己的十進位 <xref:System.Windows.Forms.Control.TabIndex%2A> 值，並以 .0 開始。  很自然的，當 <xref:System.Windows.Forms.GroupBox> 控制項的 <xref:System.Windows.Forms.Control.TabIndex%2A> 值增加，它內部的控制項也將增加。  假如您將 <xref:System.Windows.Forms.Control.TabIndex%2A> 的值從 5 變成 6，群組內第一個控制項的 <xref:System.Windows.Forms.Control.TabIndex%2A> 值自動改變為 6.0，以此類推。  
  
 最後，您也可以讓表單上的控制項在定位順序中被略過。  通常，在執行階段連續按 TAB 鍵可選擇定位順序內的每一個控制項。  藉由關閉 <xref:System.Windows.Forms.Control.TabStop%2A> 屬性，您可以在表單的定位順序中跳過控制項。  
  
#### 若要從定位順序中移除控制項  
  
1.  在 \[屬性\] 視窗中，將控制項的 <xref:System.Windows.Forms.Control.TabStop%2A> 屬性設定為 `false`。  
  
     <xref:System.Windows.Forms.Control.TabStop%2A> 屬性設為 `false` 的控制項仍會維持它在定位順序中的位置，即使使用 TAB 鍵循環控制項時略過這個控制項也不受影響。  
  
    > [!NOTE]
    >  選項按鈕群組在執行階段有一個定位停駐點 \(Tab Stop\)。  已選取的按鈕 \(也就是說，<xref:System.Windows.Forms.RadioButton.Checked%2A> 屬性設定為 `true` 的按鈕\)，會將其 <xref:System.Windows.Forms.Control.TabStop%2A> 屬性自動設為 `true`，其他按鈕則把自己的 <xref:System.Windows.Forms.Control.TabStop%2A> 屬性設為 `false`。  如需 <xref:System.Windows.Forms.RadioButton> 控制項群組的詳細資訊，請參閱[將 Windows Form RadioButton 控制項組成集合使用](../../../../docs/framework/winforms/controls/how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)。  
  
## 請參閱  
 [Windows Form 控制項](../../../../docs/framework/winforms/controls/index.md)   
 [排列 Windows Form 上的控制項](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)   
 [在 Windows Form 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)   
 [依功能區分 Windows Form 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)