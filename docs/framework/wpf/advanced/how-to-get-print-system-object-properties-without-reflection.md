---
title: "如何：取得列印系統物件屬性但不使用反映"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: PrintSystemObject [WPF], getting properties
ms.assetid: 43560f28-183d-41c1-b9d1-de7c2552273e
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2f6015d25ee8868fe9b4c6dcf3bf145d413521e1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-print-system-object-properties-without-reflection"></a><span data-ttu-id="be543-102">如何：取得列印系統物件屬性但不使用反映</span><span class="sxs-lookup"><span data-stu-id="be543-102">How to: Get Print System Object Properties Without Reflection</span></span>
<span data-ttu-id="be543-103">使用反映詳細列出的物件上的屬性 （和這些屬性的類型） 不會降低應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="be543-103">Using reflection to itemize the properties (and the types of those properties) on an object can slow application performance.</span></span> <span data-ttu-id="be543-104"><xref:System.Printing.IndexedProperties>命名空間提供方法來取得這項資訊與使用反映。</span><span class="sxs-lookup"><span data-stu-id="be543-104">The <xref:System.Printing.IndexedProperties> namespace provides a means to getting this information with using reflection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be543-105">範例</span><span class="sxs-lookup"><span data-stu-id="be543-105">Example</span></span>  
 <span data-ttu-id="be543-106">執行此作業的步驟如下所示。</span><span class="sxs-lookup"><span data-stu-id="be543-106">The steps for doing this are as follows.</span></span>  
  
1.  <span data-ttu-id="be543-107">建立類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="be543-107">Create an instance of the type.</span></span> <span data-ttu-id="be543-108">在下列範例中，此類型是<xref:System.Printing.PrintQueue>隨附的型別[!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)]，但是幾乎完全相同的程式碼應能用於類型衍生自<xref:System.Printing.PrintSystemObject>。</span><span class="sxs-lookup"><span data-stu-id="be543-108">In the example below, the type is the <xref:System.Printing.PrintQueue> type that ships with [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)], but nearly identical code should work for types that you derive from <xref:System.Printing.PrintSystemObject>.</span></span>  
  
2.  <span data-ttu-id="be543-109">建立<xref:System.Printing.IndexedProperties.PrintPropertyDictionary>的型別<xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>。</span><span class="sxs-lookup"><span data-stu-id="be543-109">Create a <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> from the type's <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>.</span></span> <span data-ttu-id="be543-110"><xref:System.Collections.DictionaryEntry.Value%2A>此字典中的每個項目的屬性是物件的其中一個衍生自類型<xref:System.Printing.IndexedProperties.PrintProperty>。</span><span class="sxs-lookup"><span data-stu-id="be543-110">The <xref:System.Collections.DictionaryEntry.Value%2A> property of each entry in this dictionary is an object of one of the types derived from <xref:System.Printing.IndexedProperties.PrintProperty>.</span></span>  
  
3.  <span data-ttu-id="be543-111">列舉字典的成員。</span><span class="sxs-lookup"><span data-stu-id="be543-111">Enumerate the members of the dictionary.</span></span> <span data-ttu-id="be543-112">針對每一項，執行下列作業。</span><span class="sxs-lookup"><span data-stu-id="be543-112">For each of them, do the following.</span></span>  
  
4.  <span data-ttu-id="be543-113">向上轉型至每個項目的值<xref:System.Printing.IndexedProperties.PrintProperty>並用它來建立<xref:System.Printing.IndexedProperties.PrintProperty>物件。</span><span class="sxs-lookup"><span data-stu-id="be543-113">Up-cast the value of each entry to <xref:System.Printing.IndexedProperties.PrintProperty> and use it to create a <xref:System.Printing.IndexedProperties.PrintProperty> object.</span></span>  
  
5.  <span data-ttu-id="be543-114">取得類型的<xref:System.Printing.IndexedProperties.PrintProperty.Value%2A>的每個<xref:System.Printing.IndexedProperties.PrintProperty>物件。</span><span class="sxs-lookup"><span data-stu-id="be543-114">Get the type of the <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> of each of the <xref:System.Printing.IndexedProperties.PrintProperty> object.</span></span>  
  
 [!code-csharp[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/CSharp/Program.cs#showpropertytypeswithoutreflection)]
 [!code-vb[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/visualbasic/program.vb#showpropertytypeswithoutreflection)]  
  
## <a name="see-also"></a><span data-ttu-id="be543-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be543-115">See Also</span></span>  
 <xref:System.Printing.IndexedProperties.PrintProperty>  
 <xref:System.Printing.PrintSystemObject>  
 <xref:System.Printing.IndexedProperties>  
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Collections.DictionaryEntry>  
 [<span data-ttu-id="be543-116">WPF 中的文件</span><span class="sxs-lookup"><span data-stu-id="be543-116">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="be543-117">列印概觀</span><span class="sxs-lookup"><span data-stu-id="be543-117">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)
