---
title: 作法：設定 Windows Forms NumericUpDown 控制項的格式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- NumericUpDown control [Windows Forms], formatting values
- up-down controls [Windows Forms], formatting numeric values
ms.assetid: fa7c5557-6bfb-45b2-975d-8887b23b0ba0
ms.openlocfilehash: 6db7a1b2aeb7282c3ac827cb8319706ed348fc22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949155"
---
# <a name="how-to-set-the-format-for-the-windows-forms-numericupdown-control"></a><span data-ttu-id="1ad67-102">HOW TO：設定 Windows Forms NumericUpDown 控制項的格式</span><span class="sxs-lookup"><span data-stu-id="1ad67-102">How to: Set the Format for the Windows Forms NumericUpDown Control</span></span>
<span data-ttu-id="1ad67-103">您可以設定在 Windows Forms <xref:System.Windows.Forms.NumericUpDown>控制項中顯示值的方式。</span><span class="sxs-lookup"><span data-stu-id="1ad67-103">You can configure how values are displayed in the Windows Forms <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="1ad67-104"><xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A>屬性會決定小數點後出現多少數位, 預設值為0。</span><span class="sxs-lookup"><span data-stu-id="1ad67-104">The <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property determines how many numbers appear after the decimal point; the default is 0.</span></span> <span data-ttu-id="1ad67-105">屬性會決定是否要在每三個小數位數之間插入分隔符號, 預設值`false`為。 <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A></span><span class="sxs-lookup"><span data-stu-id="1ad67-105">The <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property determines whether a separator will be inserted between every three decimal digits; the default is `false`.</span></span> <span data-ttu-id="1ad67-106">如果<xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A>屬性設定為`true`, 控制項可以顯示十六進位而不是十進位格式的值; 預設值為`false`。</span><span class="sxs-lookup"><span data-stu-id="1ad67-106">The control can display values in hexadecimal instead of decimal format, if the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property is set to `true`; the default is `false`.</span></span>  
  
### <a name="to-format-the-numeric-value"></a><span data-ttu-id="1ad67-107">若要格式化數值</span><span class="sxs-lookup"><span data-stu-id="1ad67-107">To format the numeric value</span></span>  
  
- <span data-ttu-id="1ad67-108">將<xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A>屬性設定為整數, 並<xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A>將屬性設定為`true`或`false`, 以顯示十進位值。</span><span class="sxs-lookup"><span data-stu-id="1ad67-108">Display a decimal value by setting the <xref:System.Windows.Forms.NumericUpDown.DecimalPlaces%2A> property to an integer and setting the <xref:System.Windows.Forms.NumericUpDown.ThousandsSeparator%2A> property to `true` or `false`.</span></span>  
  
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
  
     <span data-ttu-id="1ad67-109">-或-</span><span class="sxs-lookup"><span data-stu-id="1ad67-109">-or-</span></span>  
  
- <span data-ttu-id="1ad67-110">將<xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A>屬性設定為, 以`true`顯示十六進位值。</span><span class="sxs-lookup"><span data-stu-id="1ad67-110">Display a hexadecimal value by setting the <xref:System.Windows.Forms.NumericUpDown.Hexadecimal%2A> property to `true`.</span></span>  
  
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
    > <span data-ttu-id="1ad67-111">即使值在表單上顯示為十六進位, 在<xref:System.Windows.Forms.NumericUpDown.Value%2A>屬性上執行的任何測試都會測試其十進位值。</span><span class="sxs-lookup"><span data-stu-id="1ad67-111">Even if the value is displayed on the form as hexadecimal, any tests you perform on the <xref:System.Windows.Forms.NumericUpDown.Value%2A> property will be testing its decimal value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ad67-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ad67-112">See also</span></span>

- <xref:System.Windows.Forms.NumericUpDown>
- [<span data-ttu-id="1ad67-113">NumericUpDown 控制項</span><span class="sxs-lookup"><span data-stu-id="1ad67-113">NumericUpDown Control</span></span>](numericupdown-control-windows-forms.md)
- [<span data-ttu-id="1ad67-114">NumericUpDown 控制項概觀</span><span class="sxs-lookup"><span data-stu-id="1ad67-114">NumericUpDown Control Overview</span></span>](numericupdown-control-overview-windows-forms.md)
