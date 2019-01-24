---
title: HOW TO：指定的成員會用於測試並行衝突
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
ms.openlocfilehash: 1007cbc0961d01574fd60ec50eb63406ec7adef9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724576"
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a><span data-ttu-id="6dee1-102">HOW TO：指定的成員會用於測試並行衝突</span><span class="sxs-lookup"><span data-stu-id="6dee1-102">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>
<span data-ttu-id="6dee1-103">套用至三個列舉的其中一個[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>屬性上的<xref:System.Data.Linq.Mapping.ColumnAttribute>屬性來指定要包含在更新中的哪些成員會檢查是否有開放式並行存取衝突的偵測。</span><span class="sxs-lookup"><span data-stu-id="6dee1-103">Apply one of three enums to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify which members are to be included in update checks for the detection of optimistic concurrency conflicts.</span></span>  
  
 <span data-ttu-id="6dee1-104"><xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 (在設計階段對應) 是與 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中的執行階段並行存取功能搭配使用。</span><span class="sxs-lookup"><span data-stu-id="6dee1-104">The <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property (mapped at design time) is used together with run-time concurrency features in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="6dee1-105">如需詳細資訊，請參閱[開放式並行存取：概觀](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="6dee1-105">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6dee1-106">只要未將成員指定為 `IsVersion=true`，原始成員值就會與目前資料庫狀態進行比較。</span><span class="sxs-lookup"><span data-stu-id="6dee1-106">Original member values are compared with the current database state as long as no member is designated as `IsVersion=true`.</span></span> <span data-ttu-id="6dee1-107">如需詳細資訊，請參閱<xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>。</span><span class="sxs-lookup"><span data-stu-id="6dee1-107">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
 <span data-ttu-id="6dee1-108">如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>。</span><span class="sxs-lookup"><span data-stu-id="6dee1-108">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a><span data-ttu-id="6dee1-109">若一律要使用這個成員來偵測衝突</span><span class="sxs-lookup"><span data-stu-id="6dee1-109">To always use this member for detecting conflicts</span></span>  
  
1.  <span data-ttu-id="6dee1-110">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="6dee1-110">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="6dee1-111">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 (Property) 值設定為 `Always`。</span><span class="sxs-lookup"><span data-stu-id="6dee1-111">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `Always`.</span></span>  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a><span data-ttu-id="6dee1-112">若永不使用這個成員來偵測衝突</span><span class="sxs-lookup"><span data-stu-id="6dee1-112">To never use this member for detecting conflicts</span></span>  
  
1.  <span data-ttu-id="6dee1-113">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="6dee1-113">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="6dee1-114">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 (Property) 值設定為 `Never`。</span><span class="sxs-lookup"><span data-stu-id="6dee1-114">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `Never`.</span></span>  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a><span data-ttu-id="6dee1-115">若只有在應用程式已變更成員的值時，才使用這個成員來偵測衝突</span><span class="sxs-lookup"><span data-stu-id="6dee1-115">To use this member for detecting conflicts only when the application has changed the value of the member</span></span>  
  
1.  <span data-ttu-id="6dee1-116">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="6dee1-116">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="6dee1-117">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> 屬性 (Property) 值設定為 `WhenChanged`。</span><span class="sxs-lookup"><span data-stu-id="6dee1-117">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> property value to `WhenChanged`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6dee1-118">範例</span><span class="sxs-lookup"><span data-stu-id="6dee1-118">Example</span></span>  
 <span data-ttu-id="6dee1-119">下列範例指定 `HomePage` 物件永遠不應該在更新檢查期間進行測試。</span><span class="sxs-lookup"><span data-stu-id="6dee1-119">The following example specifies that `HomePage` objects should never be tested during update checks.</span></span> <span data-ttu-id="6dee1-120">如需詳細資訊，請參閱<xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>。</span><span class="sxs-lookup"><span data-stu-id="6dee1-120">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6dee1-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6dee1-121">See also</span></span>
- [<span data-ttu-id="6dee1-122">如何：管理變更衝突</span><span class="sxs-lookup"><span data-stu-id="6dee1-122">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [<span data-ttu-id="6dee1-123">變更和提交資料</span><span class="sxs-lookup"><span data-stu-id="6dee1-123">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
