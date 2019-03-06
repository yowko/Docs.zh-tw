---
title: HOW TO：繫結至方法
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding to methods using ObjectDataProvider
- binding [WPF], to methods
- methods [WPF], binding to
ms.assetid: 5f55e71e-2182-42a0-88d1-700cc1427a7a
ms.openlocfilehash: 8ccba42c3e16fdda73c087afde99e9864dc4ab0e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351927"
---
# <a name="how-to-bind-to-a-method"></a><span data-ttu-id="6d242-102">HOW TO：繫結至方法</span><span class="sxs-lookup"><span data-stu-id="6d242-102">How to: Bind to a Method</span></span>
<span data-ttu-id="6d242-103">下列範例示範如何將繫結至方法，使用<xref:System.Windows.Data.ObjectDataProvider>。</span><span class="sxs-lookup"><span data-stu-id="6d242-103">The following example shows how to bind to a method using <xref:System.Windows.Data.ObjectDataProvider>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d242-104">範例</span><span class="sxs-lookup"><span data-stu-id="6d242-104">Example</span></span>  
 <span data-ttu-id="6d242-105">在此範例中，`TemperatureScale` 是一個包含方法 `ConvertTemp` 的類別，它接受兩個參數 (一個是 `double` 類型，一個是 `enum` 類型 `TempType)`，並將指定的值從一個溫度單位轉換為另一個溫度單位。</span><span class="sxs-lookup"><span data-stu-id="6d242-105">In this example, `TemperatureScale` is a class that has a method `ConvertTemp`, which takes two parameters (one of `double` and one of the `enum` type `TempType)` and converts the given value from one temperature scale to another.</span></span> <span data-ttu-id="6d242-106">在下列範例中，<xref:System.Windows.Data.ObjectDataProvider>用以具現化`TemperatureScale`物件。</span><span class="sxs-lookup"><span data-stu-id="6d242-106">In the following example, an <xref:System.Windows.Data.ObjectDataProvider> is used to instantiate the `TemperatureScale` object.</span></span> <span data-ttu-id="6d242-107">`ConvertTemp` 方法是使用兩個指定的參數呼叫。</span><span class="sxs-lookup"><span data-stu-id="6d242-107">The `ConvertTemp` method is called with two specified parameters.</span></span>  
  
 [!code-xaml[BindToMethod#WindowResources](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 <span data-ttu-id="6d242-108">現在，方法已經成為資源，就可以繫結至其結果。</span><span class="sxs-lookup"><span data-stu-id="6d242-108">Now that the method is available as a resource, you can bind to its results.</span></span> <span data-ttu-id="6d242-109">在下列範例中，<xref:System.Windows.Controls.TextBox.Text%2A>的屬性<xref:System.Windows.Controls.TextBox>並<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>的<xref:System.Windows.Controls.ComboBox>繫結至方法的兩個參數。</span><span class="sxs-lookup"><span data-stu-id="6d242-109">In the following example, the <xref:System.Windows.Controls.TextBox.Text%2A> property of the <xref:System.Windows.Controls.TextBox> and the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> of the <xref:System.Windows.Controls.ComboBox> are bound to the two parameters of the method.</span></span> <span data-ttu-id="6d242-110">這可讓使用者指定要轉換的溫度及轉換前的溫度單位。</span><span class="sxs-lookup"><span data-stu-id="6d242-110">This allows users to specify the temperature to convert and the temperature scale to convert from.</span></span> <span data-ttu-id="6d242-111">請注意，<xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>設定為`true`因為我們要繫結<xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A>屬性<xref:System.Windows.Data.ObjectDataProvider>執行個體而不是屬性的物件所包裝<xref:System.Windows.Data.ObjectDataProvider>(`TemperatureScale`物件)。</span><span class="sxs-lookup"><span data-stu-id="6d242-111">Note that <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> is set to `true` because we are binding to the <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> property of the <xref:System.Windows.Data.ObjectDataProvider> instance and not properties of the object wrapped by the <xref:System.Windows.Data.ObjectDataProvider> (the `TemperatureScale` object).</span></span>  
  
 <span data-ttu-id="6d242-112"><xref:System.Windows.Controls.ContentControl.Content%2A>的最後<xref:System.Windows.Controls.Label>當使用者修改的內容時，更新<xref:System.Windows.Controls.TextBox>或選取<xref:System.Windows.Controls.ComboBox>。</span><span class="sxs-lookup"><span data-stu-id="6d242-112">The <xref:System.Windows.Controls.ContentControl.Content%2A> of the last <xref:System.Windows.Controls.Label> updates when the user modifies the content of the <xref:System.Windows.Controls.TextBox> or the selection of the <xref:System.Windows.Controls.ComboBox>.</span></span>  
  
 [!code-xaml[BindToMethod#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 <span data-ttu-id="6d242-113">轉換器`DoubleToString`會採用雙精度浮點數，並將它轉換成的字串<xref:System.Windows.Data.IValueConverter.Convert%2A>方向 (繫結來源中要繫結目標，即<xref:System.Windows.Controls.TextBox.Text%2A>屬性)，並將轉換`string`來`double`在<xref:System.Windows.Data.IValueConverter.ConvertBack%2A>方向。</span><span class="sxs-lookup"><span data-stu-id="6d242-113">The converter `DoubleToString` takes a double and turns it into a string in the <xref:System.Windows.Data.IValueConverter.Convert%2A> direction (from the binding source to binding target, which is the <xref:System.Windows.Controls.TextBox.Text%2A> property) and converts a `string` to a `double` in the <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> direction.</span></span>  
  
 <span data-ttu-id="6d242-114">`InvalidationCharacterRule`是<xref:System.Windows.Controls.ValidationRule>，以檢查無效的字元。</span><span class="sxs-lookup"><span data-stu-id="6d242-114">The `InvalidationCharacterRule` is a <xref:System.Windows.Controls.ValidationRule> that checks for invalid characters.</span></span> <span data-ttu-id="6d242-115">預設錯誤樣板，也就是紅色框線四周<xref:System.Windows.Controls.TextBox>，會出現時輸入的值不是雙精度浮點數值，通知使用者。</span><span class="sxs-lookup"><span data-stu-id="6d242-115">The default error template, which is a red border around the <xref:System.Windows.Controls.TextBox>, appears to notify users when the input value is not a double value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d242-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d242-116">See also</span></span>
- [<span data-ttu-id="6d242-117">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="6d242-117">How-to Topics</span></span>](data-binding-how-to-topics.md)
- [<span data-ttu-id="6d242-118">繫結至列舉</span><span class="sxs-lookup"><span data-stu-id="6d242-118">Bind to an Enumeration</span></span>](how-to-bind-to-an-enumeration.md)
