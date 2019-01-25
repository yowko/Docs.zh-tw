---
title: HOW TO：擷取特定資料格式的資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], retrieving data
- DataFormats class [WPF], retrieving data
- DataObject class [WPF], retrieving data
ms.assetid: a625acf3-1144-44cd-add7-456aefc3859f
ms.openlocfilehash: d11374cbc70210e648e93a385c4a9fbca112c09f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718285"
---
# <a name="how-to-retrieve-data-in-a-particular-data-format"></a><span data-ttu-id="97b19-102">HOW TO：擷取特定資料格式的資料</span><span class="sxs-lookup"><span data-stu-id="97b19-102">How to: Retrieve Data in a Particular Data Format</span></span>
<span data-ttu-id="97b19-103">下列範例示範如何擷取指定之格式的資料物件中的資料。</span><span class="sxs-lookup"><span data-stu-id="97b19-103">The following examples show how to retrieve data from a data object in a specified format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97b19-104">範例</span><span class="sxs-lookup"><span data-stu-id="97b19-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="97b19-105">描述</span><span class="sxs-lookup"><span data-stu-id="97b19-105">Description</span></span>  
 <span data-ttu-id="97b19-106">下列範例程式碼會使用<xref:System.Windows.DataObject.GetDataPresent%28System.String%29>多載來先檢查指定的資料設定格式 （原生或自動轉換）; 如果指定的格式使用時，範例會使用擷取資料<xref:System.Windows.DataObject.GetData%28System.String%29>方法。</span><span class="sxs-lookup"><span data-stu-id="97b19-106">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> overload to first check if a specified data format is available (natively or by auto-convert); if the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="97b19-107">程式碼</span><span class="sxs-lookup"><span data-stu-id="97b19-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
## <a name="example"></a><span data-ttu-id="97b19-108">範例</span><span class="sxs-lookup"><span data-stu-id="97b19-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="97b19-109">描述</span><span class="sxs-lookup"><span data-stu-id="97b19-109">Description</span></span>  
 <span data-ttu-id="97b19-110">下列範例程式碼會使用<xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29>先檢查指定的資料格式是否可以使用原生的多載 （自動轉換的資料格式已篩選）; 如果指定的格式使用時，此範例會擷取資料使用<xref:System.Windows.DataObject.GetData%28System.String%29>方法。</span><span class="sxs-lookup"><span data-stu-id="97b19-110">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> overload to first check if a specified data format is available natively (auto-convertible data formats are filtered); if the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="97b19-111">程式碼</span><span class="sxs-lookup"><span data-stu-id="97b19-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat_native)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat_native)]  
  
## <a name="see-also"></a><span data-ttu-id="97b19-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97b19-112">See also</span></span>
- <xref:System.Windows.IDataObject>
- [<span data-ttu-id="97b19-113">拖放概觀</span><span class="sxs-lookup"><span data-stu-id="97b19-113">Drag and Drop Overview</span></span>](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
