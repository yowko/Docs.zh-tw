---
title: 作法：指定用於測試並行衝突的成員
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
ms.openlocfilehash: e774935827934ae73873247def049b4045535272
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197140"
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a><span data-ttu-id="db0f4-102">作法：指定用於測試並行衝突的成員</span><span class="sxs-lookup"><span data-stu-id="db0f4-102">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>

<span data-ttu-id="db0f4-103">將三個列舉的其中一個套用至屬性 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 上的屬性 <xref:System.Data.Linq.Mapping.ColumnAttribute> ，以指定哪些成員要包含在更新檢查中，以偵測開放式平行存取衝突。</span><span class="sxs-lookup"><span data-stu-id="db0f4-103">Apply one of three enums to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify which members are to be included in update checks for the detection of optimistic concurrency conflicts.</span></span>  
  
 <span data-ttu-id="db0f4-104"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 (在設計階段對應) 是與 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中的執行階段並行存取功能搭配使用。</span><span class="sxs-lookup"><span data-stu-id="db0f4-104">The <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property (mapped at design time) is used together with run-time concurrency features in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="db0f4-105">如需詳細資訊，請參閱 [開放式平行存取：總覽](optimistic-concurrency-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="db0f4-105">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="db0f4-106">只要未將成員指定為 `IsVersion=true`，原始成員值就會與目前資料庫狀態進行比較。</span><span class="sxs-lookup"><span data-stu-id="db0f4-106">Original member values are compared with the current database state as long as no member is designated as `IsVersion=true`.</span></span> <span data-ttu-id="db0f4-107">如需詳細資訊，請參閱<xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>。</span><span class="sxs-lookup"><span data-stu-id="db0f4-107">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
 <span data-ttu-id="db0f4-108">如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>。</span><span class="sxs-lookup"><span data-stu-id="db0f4-108">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a><span data-ttu-id="db0f4-109">若一律要使用這個成員來偵測衝突</span><span class="sxs-lookup"><span data-stu-id="db0f4-109">To always use this member for detecting conflicts</span></span>  
  
1. <span data-ttu-id="db0f4-110">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="db0f4-110">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="db0f4-111">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 (Property) 值設定為 `Always`。</span><span class="sxs-lookup"><span data-stu-id="db0f4-111">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `Always`.</span></span>  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a><span data-ttu-id="db0f4-112">若永不使用這個成員來偵測衝突</span><span class="sxs-lookup"><span data-stu-id="db0f4-112">To never use this member for detecting conflicts</span></span>  
  
1. <span data-ttu-id="db0f4-113">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="db0f4-113">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="db0f4-114">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 (Property) 值設定為 `Never`。</span><span class="sxs-lookup"><span data-stu-id="db0f4-114">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `Never`.</span></span>  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a><span data-ttu-id="db0f4-115">若只有在應用程式已變更成員的值時，才使用這個成員來偵測衝突</span><span class="sxs-lookup"><span data-stu-id="db0f4-115">To use this member for detecting conflicts only when the application has changed the value of the member</span></span>  
  
1. <span data-ttu-id="db0f4-116">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="db0f4-116">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="db0f4-117">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 (Property) 值設定為 `WhenChanged`。</span><span class="sxs-lookup"><span data-stu-id="db0f4-117">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `WhenChanged`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db0f4-118">範例</span><span class="sxs-lookup"><span data-stu-id="db0f4-118">Example</span></span>  

 <span data-ttu-id="db0f4-119">下列範例指定 `HomePage` 物件永遠不應該在更新檢查期間進行測試。</span><span class="sxs-lookup"><span data-stu-id="db0f4-119">The following example specifies that `HomePage` objects should never be tested during update checks.</span></span> <span data-ttu-id="db0f4-120">如需詳細資訊，請參閱<xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>。</span><span class="sxs-lookup"><span data-stu-id="db0f4-120">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="db0f4-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db0f4-121">See also</span></span>

- [<span data-ttu-id="db0f4-122">作法：管理變更衝突</span><span class="sxs-lookup"><span data-stu-id="db0f4-122">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="db0f4-123">變更資料和提交</span><span class="sxs-lookup"><span data-stu-id="db0f4-123">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
