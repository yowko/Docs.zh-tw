---
title: 操作說明：繫結至方法
description: 請遵循此範例來瞭解如何在 Windows Presentation Foundation （WPF）中系結至物件的方法。
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding to methods using ObjectDataProvider
- binding [WPF], to methods
- methods [WPF], binding to
ms.assetid: 5f55e71e-2182-42a0-88d1-700cc1427a7a
ms.openlocfilehash: 9501e6357203c21651e85f1d65059be1d70becf2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619594"
---
# <a name="how-to-bind-to-a-method"></a><span data-ttu-id="e117a-103">操作說明：繫結至方法</span><span class="sxs-lookup"><span data-stu-id="e117a-103">How to: Bind to a Method</span></span>
<span data-ttu-id="e117a-104">下列範例顯示如何使用系結至方法 <xref:System.Windows.Data.ObjectDataProvider> 。</span><span class="sxs-lookup"><span data-stu-id="e117a-104">The following example shows how to bind to a method using <xref:System.Windows.Data.ObjectDataProvider>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e117a-105">範例</span><span class="sxs-lookup"><span data-stu-id="e117a-105">Example</span></span>  
 <span data-ttu-id="e117a-106">在此範例中，`TemperatureScale` 是一個包含方法 `ConvertTemp` 的類別，它接受兩個參數 (一個是 `double` 類型，一個是 `enum` 類型 `TempType)`，並將指定的值從一個溫度單位轉換為另一個溫度單位。</span><span class="sxs-lookup"><span data-stu-id="e117a-106">In this example, `TemperatureScale` is a class that has a method `ConvertTemp`, which takes two parameters (one of `double` and one of the `enum` type `TempType)` and converts the given value from one temperature scale to another.</span></span> <span data-ttu-id="e117a-107">在下列範例中， <xref:System.Windows.Data.ObjectDataProvider> 會使用來具現化 `TemperatureScale` 物件。</span><span class="sxs-lookup"><span data-stu-id="e117a-107">In the following example, an <xref:System.Windows.Data.ObjectDataProvider> is used to instantiate the `TemperatureScale` object.</span></span> <span data-ttu-id="e117a-108">`ConvertTemp` 方法是使用兩個指定的參數呼叫。</span><span class="sxs-lookup"><span data-stu-id="e117a-108">The `ConvertTemp` method is called with two specified parameters.</span></span>  
  
 [!code-xaml[BindToMethod#WindowResources](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 <span data-ttu-id="e117a-109">現在，方法已經成為資源，就可以繫結至其結果。</span><span class="sxs-lookup"><span data-stu-id="e117a-109">Now that the method is available as a resource, you can bind to its results.</span></span> <span data-ttu-id="e117a-110">在下列範例中，的 <xref:System.Windows.Controls.TextBox.Text%2A> 和的屬性 <xref:System.Windows.Controls.TextBox> 會系結 <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> <xref:System.Windows.Controls.ComboBox> 至方法的兩個參數。</span><span class="sxs-lookup"><span data-stu-id="e117a-110">In the following example, the <xref:System.Windows.Controls.TextBox.Text%2A> property of the <xref:System.Windows.Controls.TextBox> and the <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> of the <xref:System.Windows.Controls.ComboBox> are bound to the two parameters of the method.</span></span> <span data-ttu-id="e117a-111">這可讓使用者指定要轉換的溫度及轉換前的溫度單位。</span><span class="sxs-lookup"><span data-stu-id="e117a-111">This allows users to specify the temperature to convert and the temperature scale to convert from.</span></span> <span data-ttu-id="e117a-112">請注意， <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> 設定為， `true` 因為我們系結至 <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> 實例的屬性 <xref:System.Windows.Data.ObjectDataProvider> ，而不是 <xref:System.Windows.Data.ObjectDataProvider> （物件）所包裝之物件的屬性 `TemperatureScale` 。</span><span class="sxs-lookup"><span data-stu-id="e117a-112">Note that <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> is set to `true` because we are binding to the <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> property of the <xref:System.Windows.Data.ObjectDataProvider> instance and not properties of the object wrapped by the <xref:System.Windows.Data.ObjectDataProvider> (the `TemperatureScale` object).</span></span>  
  
 <span data-ttu-id="e117a-113"><xref:System.Windows.Controls.ContentControl.Content%2A> <xref:System.Windows.Controls.Label> 當使用者修改的內容 <xref:System.Windows.Controls.TextBox> 或的選取專案時，最後一次更新的 <xref:System.Windows.Controls.ComboBox> 。</span><span class="sxs-lookup"><span data-stu-id="e117a-113">The <xref:System.Windows.Controls.ContentControl.Content%2A> of the last <xref:System.Windows.Controls.Label> updates when the user modifies the content of the <xref:System.Windows.Controls.TextBox> or the selection of the <xref:System.Windows.Controls.ComboBox>.</span></span>  
  
 [!code-xaml[BindToMethod#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 <span data-ttu-id="e117a-114">轉換器 `DoubleToString` 會採用雙精度浮點數，並將其轉換成 <xref:System.Windows.Data.IValueConverter.Convert%2A> 方向的字串（從系結來源到系結目標，也就是 <xref:System.Windows.Controls.TextBox.Text%2A> 屬性），並將轉換成 `string` 方向的 `double` <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> 。</span><span class="sxs-lookup"><span data-stu-id="e117a-114">The converter `DoubleToString` takes a double and turns it into a string in the <xref:System.Windows.Data.IValueConverter.Convert%2A> direction (from the binding source to binding target, which is the <xref:System.Windows.Controls.TextBox.Text%2A> property) and converts a `string` to a `double` in the <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> direction.</span></span>  
  
 <span data-ttu-id="e117a-115">`InvalidationCharacterRule`是 <xref:System.Windows.Controls.ValidationRule> ，它會檢查是否有不正確字元。</span><span class="sxs-lookup"><span data-stu-id="e117a-115">The `InvalidationCharacterRule` is a <xref:System.Windows.Controls.ValidationRule> that checks for invalid characters.</span></span> <span data-ttu-id="e117a-116">預設錯誤範本是周圍的紅色框線 <xref:System.Windows.Controls.TextBox> ，當輸入值不是雙精度值時，就會通知使用者。</span><span class="sxs-lookup"><span data-stu-id="e117a-116">The default error template, which is a red border around the <xref:System.Windows.Controls.TextBox>, appears to notify users when the input value is not a double value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e117a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e117a-117">See also</span></span>

- [<span data-ttu-id="e117a-118">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="e117a-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
- [<span data-ttu-id="e117a-119">系結至列舉</span><span class="sxs-lookup"><span data-stu-id="e117a-119">Bind to an Enumeration</span></span>](how-to-bind-to-an-enumeration.md)
