---
title: HOW TO：設定 Windows Forms NumericUpDown 控制項的格式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- NumericUpDown control [Windows Forms], formatting values
- up-down controls [Windows Forms], formatting numeric values
ms.assetid: fa7c5557-6bfb-45b2-975d-8887b23b0ba0
ms.openlocfilehash: 5957a44c7b07aa1b8d8df32667f023c0873ec1de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013188"
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a><span data-ttu-id="a3b4a-102">HOW TO：設定 Windows Forms NumericUpDown 控制項的格式</span><span class="sxs-lookup"><span data-stu-id="a3b4a-102">How to: Set the Format for the Windows Forms NumericUpDown Control</span></span>
<span data-ttu-id="a3b4a-103">您可以設定 Windows Form 中值的顯示方式<xref:System.Windows.Forms.NumericUpDown>控制項。</span><span class="sxs-lookup"><span data-stu-id="a3b4a-103">You can configure how values are displayed in the Windows Forms <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="a3b4a-104"><xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A>屬性可決定多少數字的小數點後，預設值為 0。</span><span class="sxs-lookup"><span data-stu-id="a3b4a-104">The <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property determines how many numbers appear after the decimal point; the default is 0.</span></span> <span data-ttu-id="a3b4a-105"><xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A>屬性會決定是否會每隔三個十進位數字之間插入分隔符號; 預設值是`false`。</span><span class="sxs-lookup"><span data-stu-id="a3b4a-105">The <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property determines whether a separator will be inserted between every three decimal digits; the default is `false`.</span></span> <span data-ttu-id="a3b4a-106">控制項可以顯示值以十六進位方式而不是十進位格式，如果<xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A>屬性設定為`true`; 預設值是`false`。</span><span class="sxs-lookup"><span data-stu-id="a3b4a-106">The control can display values in hexadecimal instead of decimal format, if the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property is set to `true`; the default is `false`.</span></span>  
  
### <a name="to-format-the-numeric-value"></a><span data-ttu-id="a3b4a-107">若要格式化的數值</span><span class="sxs-lookup"><span data-stu-id="a3b4a-107">To format the numeric value</span></span>  
  
-   <span data-ttu-id="a3b4a-108">藉由設定顯示十進位值<xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A>屬性設為整數並設定<xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A>屬性設`true`或`false`。</span><span class="sxs-lookup"><span data-stu-id="a3b4a-108">Display a decimal value by setting the <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property to an integer and setting the <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property to `true` or `false`.</span></span>  
  
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
  
     <span data-ttu-id="a3b4a-109">-或-</span><span class="sxs-lookup"><span data-stu-id="a3b4a-109">-or-</span></span>  
  
-   <span data-ttu-id="a3b4a-110">藉由設定顯示十六進位值<xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A>屬性設`true`。</span><span class="sxs-lookup"><span data-stu-id="a3b4a-110">Display a hexadecimal value by setting the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property to `true`.</span></span>  
  
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
    >  <span data-ttu-id="a3b4a-111">即使值顯示為十六進位形式，任何測試您對<xref:System.Windows.Forms.NumericUpDown.Value%2A>屬性將會測試其十進位值。</span><span class="sxs-lookup"><span data-stu-id="a3b4a-111">Even if the value is displayed on the form as hexadecimal, any tests you perform on the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property will be testing its decimal value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3b4a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3b4a-112">See also</span></span>

- <xref:System.Windows.Forms.NumericUpDown>
- [<span data-ttu-id="a3b4a-113">NumericUpDown 控制項</span><span class="sxs-lookup"><span data-stu-id="a3b4a-113">NumericUpDown Control</span></span>](numericupdown-control-windows-forms.md)
- [<span data-ttu-id="a3b4a-114">NumericUpDown 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="a3b4a-114">NumericUpDown Control Overview</span></span>](numericupdown-control-overview-windows-forms.md)
