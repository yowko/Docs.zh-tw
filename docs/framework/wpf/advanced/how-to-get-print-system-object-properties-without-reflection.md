---
title: HOW TO：取得列印系統物件屬性但不使用反映
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PrintSystemObject [WPF], getting properties
ms.assetid: 43560f28-183d-41c1-b9d1-de7c2552273e
ms.openlocfilehash: b03be30422a93980ecdbcdbd428600fd41abd824
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367579"
---
# <a name="how-to-get-print-system-object-properties-without-reflection"></a><span data-ttu-id="36d92-102">HOW TO：取得列印系統物件屬性但不使用反映</span><span class="sxs-lookup"><span data-stu-id="36d92-102">How to: Get Print System Object Properties Without Reflection</span></span>
<span data-ttu-id="36d92-103">使用反映來詳細列出的物件上的屬性 （和這些屬性的類型） 可能會降低應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="36d92-103">Using reflection to itemize the properties (and the types of those properties) on an object can slow application performance.</span></span> <span data-ttu-id="36d92-104"><xref:System.Printing.IndexedProperties>命名空間提供一個方法來取得這項資訊搭配使用反映。</span><span class="sxs-lookup"><span data-stu-id="36d92-104">The <xref:System.Printing.IndexedProperties> namespace provides a means to getting this information with using reflection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36d92-105">範例</span><span class="sxs-lookup"><span data-stu-id="36d92-105">Example</span></span>  
 <span data-ttu-id="36d92-106">執行此動作的步驟如下所示。</span><span class="sxs-lookup"><span data-stu-id="36d92-106">The steps for doing this are as follows.</span></span>  
  
1.  <span data-ttu-id="36d92-107">建立型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="36d92-107">Create an instance of the type.</span></span> <span data-ttu-id="36d92-108">在下列範例中，類型是<xref:System.Printing.PrintQueue>隨附於 Microsoft.NET Framework，但幾乎完全相同的程式碼的類型應該適用於類型衍生自<xref:System.Printing.PrintSystemObject>。</span><span class="sxs-lookup"><span data-stu-id="36d92-108">In the example below, the type is the <xref:System.Printing.PrintQueue> type that ships with Microsoft .NET Framework, but nearly identical code should work for types that you derive from <xref:System.Printing.PrintSystemObject>.</span></span>  
  
2.  <span data-ttu-id="36d92-109">建立<xref:System.Printing.IndexedProperties.PrintPropertyDictionary>的型別<xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>。</span><span class="sxs-lookup"><span data-stu-id="36d92-109">Create a <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> from the type's <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>.</span></span> <span data-ttu-id="36d92-110"><xref:System.Collections.DictionaryEntry.Value%2A>這個字典中的每個項目屬性是其中一個衍生自型別的物件<xref:System.Printing.IndexedProperties.PrintProperty>。</span><span class="sxs-lookup"><span data-stu-id="36d92-110">The <xref:System.Collections.DictionaryEntry.Value%2A> property of each entry in this dictionary is an object of one of the types derived from <xref:System.Printing.IndexedProperties.PrintProperty>.</span></span>  
  
3.  <span data-ttu-id="36d92-111">列舉成員的字典。</span><span class="sxs-lookup"><span data-stu-id="36d92-111">Enumerate the members of the dictionary.</span></span> <span data-ttu-id="36d92-112">為每個，請執行下列項目。</span><span class="sxs-lookup"><span data-stu-id="36d92-112">For each of them, do the following.</span></span>  
  
4.  <span data-ttu-id="36d92-113">向上轉型至每個項目的值<xref:System.Printing.IndexedProperties.PrintProperty>並使用它來建立<xref:System.Printing.IndexedProperties.PrintProperty>物件。</span><span class="sxs-lookup"><span data-stu-id="36d92-113">Up-cast the value of each entry to <xref:System.Printing.IndexedProperties.PrintProperty> and use it to create a <xref:System.Printing.IndexedProperties.PrintProperty> object.</span></span>  
  
5.  <span data-ttu-id="36d92-114">取得的型別<xref:System.Printing.IndexedProperties.PrintProperty.Value%2A>的每個<xref:System.Printing.IndexedProperties.PrintProperty>物件。</span><span class="sxs-lookup"><span data-stu-id="36d92-114">Get the type of the <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> of each of the <xref:System.Printing.IndexedProperties.PrintProperty> object.</span></span>  
  
 [!code-csharp[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](~/samples/snippets/csharp/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/CSharp/Program.cs#showpropertytypeswithoutreflection)]
 [!code-vb[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/visualbasic/program.vb#showpropertytypeswithoutreflection)]  
  
## <a name="see-also"></a><span data-ttu-id="36d92-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36d92-115">See also</span></span>
- <xref:System.Printing.IndexedProperties.PrintProperty>
- <xref:System.Printing.PrintSystemObject>
- <xref:System.Printing.IndexedProperties>
- <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.PrintQueue>
- <xref:System.Collections.DictionaryEntry>
- [<span data-ttu-id="36d92-116">WPF 中的文件</span><span class="sxs-lookup"><span data-stu-id="36d92-116">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="36d92-117">列印概觀</span><span class="sxs-lookup"><span data-stu-id="36d92-117">Printing Overview</span></span>](printing-overview.md)
