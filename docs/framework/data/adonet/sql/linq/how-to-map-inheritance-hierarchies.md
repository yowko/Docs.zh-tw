---
title: "如何：對應繼承階層架構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 93f3eb40e96c0735218464c8ee69a3e6fe358a03
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-map-inheritance-hierarchies"></a><span data-ttu-id="dc3fd-102">如何：對應繼承階層架構</span><span class="sxs-lookup"><span data-stu-id="dc3fd-102">How to: Map Inheritance Hierarchies</span></span>
<span data-ttu-id="dc3fd-103">若要在 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 中實作繼承對應，您必須如下列步驟所述，在繼承階層架構 (Inheritance Hierarchy) 的根類別上指定屬性 (Attribute) 與其屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="dc3fd-103">To implement inheritance mapping in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)], you must specify the attributes and attribute properties on the root class of the inheritance hierarchy as described in the following steps.</span></span> <span data-ttu-id="dc3fd-104">使用 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 的開發人員可以使用 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] 來對應繼承階層架構。</span><span class="sxs-lookup"><span data-stu-id="dc3fd-104">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map inheritance hierarchies.</span></span> <span data-ttu-id="dc3fd-105">請參閱[How to： 使用 O/R 設計工具設定繼承](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)。</span><span class="sxs-lookup"><span data-stu-id="dc3fd-105">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc3fd-106">子類別上不需要任何特別的屬性 (Attribute) 或屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="dc3fd-106">No special attributes or properties are required on the subclasses.</span></span> <span data-ttu-id="dc3fd-107">請特別注意，子類別沒有 <xref:System.Data.Linq.Mapping.TableAttribute> 屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="dc3fd-107">Note especially that subclasses do not have the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span>  
  
### <a name="to-map-an-inheritance-hierarchy"></a><span data-ttu-id="dc3fd-108">若要對應繼承階層架構</span><span class="sxs-lookup"><span data-stu-id="dc3fd-108">To map an inheritance hierarchy</span></span>  
  
1.  <span data-ttu-id="dc3fd-109">將 <xref:System.Data.Linq.Mapping.TableAttribute> 屬性 (Attribute) 加入至根類別。</span><span class="sxs-lookup"><span data-stu-id="dc3fd-109">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the root class.</span></span>  
  
2.  <span data-ttu-id="dc3fd-110">同樣在根類別中，加入階層結構中每個類別的 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="dc3fd-110">Also to the root class, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute for each class in the hierarchy structure.</span></span>  
  
3.  <span data-ttu-id="dc3fd-111">針對每個 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 屬性 (Attribute)，定義 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> 屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="dc3fd-111">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, define a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> property.</span></span>  
  
     <span data-ttu-id="dc3fd-112">這個屬性 (Property) 保留的值會顯示在資料庫資料表的 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> 資料行中，以表示此資料列屬於哪個類別或子類別。</span><span class="sxs-lookup"><span data-stu-id="dc3fd-112">This property holds a value that appears in the database table in the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> column to indicate which class or subclass this row of data belongs to.</span></span>  
  
4.  <span data-ttu-id="dc3fd-113">針對每個 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 屬性 (Attribute)，同時加入 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> 屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="dc3fd-113">For each <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attribute, also add a <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> property.</span></span>  
  
     <span data-ttu-id="dc3fd-114">這個屬性 (Property) 保留的值會指定索引鍵值所表示的類別或子類別。</span><span class="sxs-lookup"><span data-stu-id="dc3fd-114">This property holds a value that specifies which class or subclass the key value signifies.</span></span>  
  
5.  <span data-ttu-id="dc3fd-115">僅在其中一個 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 屬性 (Attribute) 中，加入 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> 屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="dc3fd-115">On only one of the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> attributes, add an <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> property.</span></span>  
  
     <span data-ttu-id="dc3fd-116">這個屬性是用來指定*後援*對應時資料庫資料表中的鑑別子值不符合任何<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>繼承對應中的值。</span><span class="sxs-lookup"><span data-stu-id="dc3fd-116">This property serves to designate a *fallback* mapping when the discriminator value from the database table does not match any <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value in the inheritance mappings.</span></span>  
  
6.  <span data-ttu-id="dc3fd-117">加入 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> 屬性 (Attribute) 的 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="dc3fd-117">Add an <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> property for a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
     <span data-ttu-id="dc3fd-118">這個屬性 (Property) 表示此為保留 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> 值的資料行。</span><span class="sxs-lookup"><span data-stu-id="dc3fd-118">This property signifies that this is the column that holds the <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc3fd-119">範例</span><span class="sxs-lookup"><span data-stu-id="dc3fd-119">Example</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc3fd-120">如果您使用的是 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)]，就可以使用 [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] 來設定繼承。</span><span class="sxs-lookup"><span data-stu-id="dc3fd-120">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to configure inheritance.</span></span> <span data-ttu-id="dc3fd-121">請參閱[How to： 使用 O/R 設計工具設定繼承](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span><span class="sxs-lookup"><span data-stu-id="dc3fd-121">See [How to: Configure inheritance by using the O/R Designer](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)</span></span>  
  
 <span data-ttu-id="dc3fd-122">在下列程式碼範例中，`Vehicle` 會定義為根類別，而且會實作先前的步驟以描述 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 的階層架構。</span><span class="sxs-lookup"><span data-stu-id="dc3fd-122">In the following code example, `Vehicle` is defined as the root class, and the previous steps have been implemented to describe the hierarchy for [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span>  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="dc3fd-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="dc3fd-123">See Also</span></span>  
 [<span data-ttu-id="dc3fd-124">繼承支援</span><span class="sxs-lookup"><span data-stu-id="dc3fd-124">Inheritance Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md)  
 [<span data-ttu-id="dc3fd-125">如何：使用程式碼編輯器自訂實體類別</span><span class="sxs-lookup"><span data-stu-id="dc3fd-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
