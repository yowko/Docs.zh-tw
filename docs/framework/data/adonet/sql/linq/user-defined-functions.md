---
title: 使用者定義函式
ms.date: 03/30/2017
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
ms.openlocfilehash: f1222d9332d365c9c3c6ca2aa28cbb48e92c04e0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61917653"
---
# <a name="user-defined-functions"></a><span data-ttu-id="b512b-102">使用者定義函式</span><span class="sxs-lookup"><span data-stu-id="b512b-102">User-Defined Functions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="b512b-103">會使用物件模型 (Object Model) 中的方法來表示使用者定義函式。</span><span class="sxs-lookup"><span data-stu-id="b512b-103">uses methods in your object model to represent user-defined functions.</span></span> <span data-ttu-id="b512b-104">您可套用 <xref:System.Data.Linq.Mapping.FunctionAttribute> 屬性 (Attribute) 和 (視需要) 套用 <xref:System.Data.Linq.Mapping.ParameterAttribute> 屬性，將方法指定為函式。</span><span class="sxs-lookup"><span data-stu-id="b512b-104">You designate methods as functions by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="b512b-105">如需詳細資訊，請參閱 < [LINQ to SQL 物件模型](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)。</span><span class="sxs-lookup"><span data-stu-id="b512b-105">For more information, see [The LINQ to SQL Object Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="b512b-106">若要避免 <xref:System.InvalidOperationException>，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中的使用者定義函式必須為下列其中一種形式：</span><span class="sxs-lookup"><span data-stu-id="b512b-106">To avoid an <xref:System.InvalidOperationException>, user-defined functions in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] must be in one of the following forms:</span></span>  
  
-   <span data-ttu-id="b512b-107">包裝為具有正確對應屬性之方法呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="b512b-107">A function wrapped as a method call having the correct mapping attributes.</span></span> <span data-ttu-id="b512b-108">如需詳細資訊，請參閱 <<c0> [ 屬性為基礎的對應](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="b512b-108">For more information, see [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
-   <span data-ttu-id="b512b-109">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 特有的靜態 SQL 方法。</span><span class="sxs-lookup"><span data-stu-id="b512b-109">A static SQL method specific to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
-   <span data-ttu-id="b512b-110">[!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] 方法所支援的函式。</span><span class="sxs-lookup"><span data-stu-id="b512b-110">A function supported by a [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] method.</span></span>  
  
 <span data-ttu-id="b512b-111">本節中的主題顯示自行撰寫程式碼時，如何在應用程式中形成和呼叫這些方法。</span><span class="sxs-lookup"><span data-stu-id="b512b-111">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span> <span data-ttu-id="b512b-112">使用 Visual Studio 的開發人員通常會使用[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]對應使用者定義函式。</span><span class="sxs-lookup"><span data-stu-id="b512b-112">Developers using Visual Studio would typically use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map user-defined functions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b512b-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="b512b-113">In This Section</span></span>  
 [<span data-ttu-id="b512b-114">如何：使用純量值使用者定義函式</span><span class="sxs-lookup"><span data-stu-id="b512b-114">How to: Use Scalar-Valued User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-scalar-valued-user-defined-functions.md)  
 <span data-ttu-id="b512b-115">描述如何實作可傳回純量值的函式。</span><span class="sxs-lookup"><span data-stu-id="b512b-115">Describes how to implement a function that returns scalar values.</span></span>  
  
 [<span data-ttu-id="b512b-116">如何：使用資料表值使用者定義函式</span><span class="sxs-lookup"><span data-stu-id="b512b-116">How to: Use Table-Valued User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-table-valued-user-defined-functions.md)  
 <span data-ttu-id="b512b-117">描述如何實作可傳回資料表值的函式。</span><span class="sxs-lookup"><span data-stu-id="b512b-117">Describes how to implement a function that returns table values.</span></span>  
  
 [<span data-ttu-id="b512b-118">如何：使用者定義函式內嵌方式呼叫</span><span class="sxs-lookup"><span data-stu-id="b512b-118">How to: Call User-Defined Functions Inline</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)  
 <span data-ttu-id="b512b-119">描述如何對函式進行內嵌 (Inline) 呼叫，以及當呼叫成為內嵌時的執行差異。</span><span class="sxs-lookup"><span data-stu-id="b512b-119">Describes how to make inline calls to functions and the differences in execution when the call is made inline.</span></span>
