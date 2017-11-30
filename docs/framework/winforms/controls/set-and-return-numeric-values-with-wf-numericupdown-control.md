---
title: "如何：使用 Windows Form NumericUpDown 控制項設定和傳回數值"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- numeric values [Windows Forms], Windows Forms
- Windows Forms, numeric values
- Windows Forms controls, NumericUpDown
- NumericUpDown control [Windows Forms], setting and returning values
ms.assetid: 5bd8f8cd-4c12-49ea-9cc3-2a647d064689
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b7bd296fb8a761527e132aecfed9310208f56222
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-and-return-numeric-values-with-the-windows-forms-numericupdown-control"></a><span data-ttu-id="3f2f6-102">如何：使用 Windows Form NumericUpDown 控制項設定和傳回數值</span><span class="sxs-lookup"><span data-stu-id="3f2f6-102">How to: Set and Return Numeric Values with the Windows Forms NumericUpDown Control</span></span>
<span data-ttu-id="3f2f6-103">Windows Form 的數值<xref:System.Windows.Forms.NumericUpDown>控制項由其<xref:System.Windows.Forms.NumericUpDown.Value%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="3f2f6-103">The numeric value of the Windows Forms <xref:System.Windows.Forms.NumericUpDown> control is determined by its <xref:System.Windows.Forms.NumericUpDown.Value%2A> property.</span></span> <span data-ttu-id="3f2f6-104">您可以如同任何其他屬性撰寫條件測試控制項的值。</span><span class="sxs-lookup"><span data-stu-id="3f2f6-104">You can write conditional tests for the control's value just as with any other property.</span></span> <span data-ttu-id="3f2f6-105">一次<xref:System.Windows.Forms.NumericUpDown.Value%2A>屬性設定，您可以調整它直接撰寫程式碼執行作業，或可以呼叫<xref:System.Windows.Forms.NumericUpDown.UpButton%2A>和<xref:System.Windows.Forms.NumericUpDown.DownButton%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="3f2f6-105">Once the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property is set, you can adjust it directly by writing code to perform operations on it, or you can call the <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> and <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> methods.</span></span>  
  
### <a name="to-set-the-numeric-value"></a><span data-ttu-id="3f2f6-106">若要設定的數值</span><span class="sxs-lookup"><span data-stu-id="3f2f6-106">To set the numeric value</span></span>  
  
1.  <span data-ttu-id="3f2f6-107">指派值給<xref:System.Windows.Forms.NumericUpDown.Value%2A>在程式碼，或在 [屬性] 視窗中的屬性。</span><span class="sxs-lookup"><span data-stu-id="3f2f6-107">Assign a value to the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property in code or in the Properties window.</span></span>  
  
    ```vb  
    NumericUpDown1.Value = 55  
    ```  
  
    ```csharp  
    numericUpDown1.Value = 55;  
    ```  
  
    ```cpp  
    numericUpDown1->Value = 55;  
    ```  
  
     <span data-ttu-id="3f2f6-108">-或-</span><span class="sxs-lookup"><span data-stu-id="3f2f6-108">-or-</span></span>  
  
2.  <span data-ttu-id="3f2f6-109">呼叫<xref:System.Windows.Forms.NumericUpDown.UpButton%2A>或<xref:System.Windows.Forms.NumericUpDown.DownButton%2A>方法，以增加或減少值中指定的數量<xref:System.Windows.Forms.NumericUpDown.Increment%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="3f2f6-109">Call the <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> or <xref:System.Windows.Forms.NumericUpDown.DownButton%2A> method to increase or decrease the value by the amount specified in the <xref:System.Windows.Forms.NumericUpDown.Increment%2A> property.</span></span>  
  
    ```vb  
    NumericUpDown1.UpButton()  
    ```  
  
    ```csharp  
    numericUpDown1.UpButton();  
    ```  
  
    ```cpp  
    numericUpDown1->UpButton();  
    ```  
  
### <a name="to-return-the-numeric-value"></a><span data-ttu-id="3f2f6-110">要傳回的數值</span><span class="sxs-lookup"><span data-stu-id="3f2f6-110">To return the numeric value</span></span>  
  
-   <span data-ttu-id="3f2f6-111">存取<xref:System.Windows.Forms.NumericUpDown.Value%2A>程式碼中的屬性。</span><span class="sxs-lookup"><span data-stu-id="3f2f6-111">Access the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property in code.</span></span>  
  
    ```vb  
    If NumericUpDown1.Value >= 65 Then  
       MessageBox.Show("Age is: " & NumericUpDown1.Value.ToString)  
    Else  
       MessageBox.Show("The customer is ineligible for a senior citizen discount.")  
    End If  
    ```  
  
    ```csharp  
    if(numericUpDown1.Value >= 65)  
    {  
       MessageBox.Show("Age is: " + numericUpDown1.Value.ToString());  
    }  
    else  
    {  
       MessageBox.Show("The customer is ineligible for a senior citizen discount.");  
    }  
    ```  
  
    ```cpp  
    if(numericUpDown1->Value >= 65)  
    {  
       MessageBox::Show(String::Concat("Age is: ",  
          numericUpDown1->Value.ToString()));  
    }  
    else  
    {  
       MessageBox::Show  
          ("The customer is ineligible for a senior citizen discount.");  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3f2f6-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f2f6-112">See Also</span></span>  
 <xref:System.Windows.Forms.NumericUpDown>  
 <xref:System.Windows.Forms.NumericUpDown.Value%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.NumericUpDown.Increment%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.NumericUpDown.UpButton%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.NumericUpDown.DownButton%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="3f2f6-113">NumericUpDown 控制項</span><span class="sxs-lookup"><span data-stu-id="3f2f6-113">NumericUpDown Control</span></span>](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)  
 [<span data-ttu-id="3f2f6-114">NumericUpDown 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="3f2f6-114">NumericUpDown Control Overview</span></span>](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md)
