---
title: HOW TO：以程式設計方式變更內容的 FlowDirection
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- FlowDirection property [WPF], changing programmatically
- documents [WPF], changing FlowDirection property programmatically
ms.assetid: 02f5a8ba-f8c0-4e5a-84b9-4c5bf12922a2
ms.openlocfilehash: ec159ed0efce8b5514788331e8715a55e7a8a638
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776554"
---
# <a name="how-to-change-the-flowdirection-of-content-programmatically"></a><span data-ttu-id="54172-102">HOW TO：以程式設計方式變更內容的 FlowDirection</span><span class="sxs-lookup"><span data-stu-id="54172-102">How to: Change the FlowDirection of Content Programmatically</span></span>
<span data-ttu-id="54172-103">此範例示範如何以程式設計方式變更<xref:System.Windows.FrameworkElement.FlowDirection%2A>屬性<xref:System.Windows.Controls.FlowDocumentReader>。</span><span class="sxs-lookup"><span data-stu-id="54172-103">This example shows how to programmatically change the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property of a <xref:System.Windows.Controls.FlowDocumentReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54172-104">範例</span><span class="sxs-lookup"><span data-stu-id="54172-104">Example</span></span>  
 <span data-ttu-id="54172-105">兩個<xref:System.Windows.Controls.Button>建立項目，每個均代表的可能值的其中一個<xref:System.Windows.FlowDirection>。</span><span class="sxs-lookup"><span data-stu-id="54172-105">Two <xref:System.Windows.Controls.Button> elements are created, each representing one of the possible values of <xref:System.Windows.FlowDirection>.</span></span> <span data-ttu-id="54172-106">當按一下按鈕時，相關聯的屬性值會套用至的內容<xref:System.Windows.Controls.FlowDocumentReader>名為`tf1`。</span><span class="sxs-lookup"><span data-stu-id="54172-106">When a button is clicked, the associated property value is applied to the contents of a <xref:System.Windows.Controls.FlowDocumentReader> named `tf1`.</span></span>  <span data-ttu-id="54172-107">屬性值也會寫入<xref:System.Windows.Controls.TextBlock>名為`txt1`。</span><span class="sxs-lookup"><span data-stu-id="54172-107">The property value is also written to a <xref:System.Windows.Controls.TextBlock> named `txt1`.</span></span>  
  
 [!code-xaml[FlowDirectionSnippets#_FlowDirectionXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml#_flowdirectionxaml)]  
  
## <a name="example"></a><span data-ttu-id="54172-108">範例</span><span class="sxs-lookup"><span data-stu-id="54172-108">Example</span></span>  
 <span data-ttu-id="54172-109">按下按鈕即可上面定義相關聯的事件處理C#程式碼後置檔案。</span><span class="sxs-lookup"><span data-stu-id="54172-109">The events associated with the button clicks defined above are handled in a C# code-behind file.</span></span>  
  
 [!code-csharp[FlowDirectionSnippets#_FlowDirection](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml.cs#_flowdirection)]
 [!code-vb[FlowDirectionSnippets#_FlowDirection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDirectionSnippets/VisualBasic/Window1.xaml.vb#_flowdirection)]
