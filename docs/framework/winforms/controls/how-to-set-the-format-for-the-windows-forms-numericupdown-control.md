---
title: "如何：為 Windows Form NumericUpDown 控制項設定格式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "NumericUpDown 控制項 [Windows Form], 格式化值"
  - "上下按鈕控制項, 格式化數值"
ms.assetid: fa7c5557-6bfb-45b2-975d-8887b23b0ba0
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：為 Windows Form NumericUpDown 控制項設定格式
您可以設定數值在 Windows Form <xref:System.Windows.Forms.NumericUpDown> 控制項中顯示的方式。  <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> 屬性決定小數點後出現的位數；預設值為 0。  <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> 屬性決定每三個十進位數字之間是否要插入分隔符號；預設值為 `false`。  當 <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> 屬性設定為 `true` 時，這個控制項可用十六進位顯示數值，而不是以十進位格式；該屬性預設值為 `false`。  
  
### 若要格式化數值  
  
-   將 <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> 屬性設定為整數並將 <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> 屬性設定成 `true` 或 `false`，即可顯示十進位數值。  
  
    ```vb  
    NumericUpDown1.DecimalPlaces = 2  
    NumericUpDown1.ThousandsSeparator = True  
  
    ```  
  
    ```csharp  
    numericUpDown1.DecimalPlaces = 2;  
    numericUpDown1.ThousandsSeparator = true;  
  
    ```  
  
    ```cpp  
    numericUpDown1->DecimalPlaces = 2;  
    numericUpDown1->ThousandsSeparator = true;  
    ```  
  
     \-或\-  
  
-   將 <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> 屬性設定成 `true`，即可顯示十六進位數值。  
  
    ```vb  
    NumericUpDown1.Hexadecimal = True  
  
    ```  
  
    ```csharp  
    numericUpDown1.Hexadecimal = true;  
  
    ```  
  
    ```cpp  
    numericUpDown1->Hexadecimal = true;  
    ```  
  
    > [!NOTE]
    >  即使表單中的值顯示為十六進位，您對 <xref:System.Windows.Forms.NumericUpDown.Value%2A> 屬性執行的任何測試都還是測試其十進位值。  
  
## 請參閱  
 <xref:System.Windows.Forms.NumericUpDown>   
 [NumericUpDown 控制項](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)   
 [NumericUpDown 控制項概觀](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md)