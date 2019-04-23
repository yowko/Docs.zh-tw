---
title: HOW TO：使用 ThicknessConverter 物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- border thickness [WPF]
- ThicknessConverter objects [WPF]
ms.assetid: 52682194-d7fd-499c-8005-73fcc84e7b2c
ms.openlocfilehash: ebfb8642a01f6d602f4e5ffa58fde6a8ee0b4e1f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59075947"
---
# <a name="how-to-use-a-thicknessconverter-object"></a><span data-ttu-id="0f54a-102">HOW TO：使用 ThicknessConverter 物件</span><span class="sxs-lookup"><span data-stu-id="0f54a-102">How to: Use a ThicknessConverter Object</span></span>
## <a name="example"></a><span data-ttu-id="0f54a-103">範例</span><span class="sxs-lookup"><span data-stu-id="0f54a-103">Example</span></span>  
 <span data-ttu-id="0f54a-104">此範例示範如何建立的執行個體<xref:System.Windows.ThicknessConverter>並用它來變更框線的粗細。</span><span class="sxs-lookup"><span data-stu-id="0f54a-104">This example shows how to create an instance of <xref:System.Windows.ThicknessConverter> and use it to change the thickness of a border.</span></span>  
  
 <span data-ttu-id="0f54a-105">此範例會定義呼叫的自訂方法`changeThickness`; 這個方法會先將轉換的內容<xref:System.Windows.Controls.ListBoxItem>，因為定義於個別[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案，以執行個體<xref:System.Windows.Thickness>，並稍後將轉換成內容<xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="0f54a-105">The example defines a custom method called `changeThickness`; this method first converts the contents of a <xref:System.Windows.Controls.ListBoxItem>, as defined in a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file, to an instance of <xref:System.Windows.Thickness>, and later converts the content into a <xref:System.String>.</span></span> <span data-ttu-id="0f54a-106">此方法會傳遞<xref:System.Windows.Controls.ListBoxItem>要<xref:System.Windows.ThicknessConverter>物件，然後將轉換<xref:System.Windows.Controls.ContentControl.Content%2A>的<xref:System.Windows.Controls.ListBoxItem>的執行個體<xref:System.Windows.Thickness>。</span><span class="sxs-lookup"><span data-stu-id="0f54a-106">This method passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.ThicknessConverter> object, which converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Windows.Thickness>.</span></span> <span data-ttu-id="0f54a-107">此值接著會傳遞的值<xref:System.Windows.Controls.Border.BorderThickness%2A>屬性<xref:System.Windows.Controls.Border>。</span><span class="sxs-lookup"><span data-stu-id="0f54a-107">This value is then passed back as the value of the <xref:System.Windows.Controls.Border.BorderThickness%2A> property of the <xref:System.Windows.Controls.Border>.</span></span>  
  
 <span data-ttu-id="0f54a-108">此範例不會執行。</span><span class="sxs-lookup"><span data-stu-id="0f54a-108">This example does not run.</span></span>  
  
 [!code-csharp[ThicknessConverter#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ThicknessConverter/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ThicknessConverter#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ThicknessConverter/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0f54a-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f54a-109">See also</span></span>

- <xref:System.Windows.Thickness>
- <xref:System.Windows.ThicknessConverter>
- <xref:System.Windows.Controls.Border>
- <span data-ttu-id="0f54a-110">[如何：變更邊界屬性](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms750561(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="0f54a-110">[How to: Change the Margin Property](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms750561(v=vs.90))</span></span>
- <span data-ttu-id="0f54a-111">[如何：轉換成新的資料類型的 ListBoxItem](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms749147(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="0f54a-111">[How to: Convert a ListBoxItem to a new Data Type](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms749147(v=vs.90))</span></span>
- [<span data-ttu-id="0f54a-112">面板概觀</span><span class="sxs-lookup"><span data-stu-id="0f54a-112">Panels Overview</span></span>](../controls/panels-overview.md)
