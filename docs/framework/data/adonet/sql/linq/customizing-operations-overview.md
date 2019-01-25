---
title: 自訂作業：總覽
ms.date: 03/30/2017
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
ms.openlocfilehash: 4f13bed76ad2814d669f487b57ae9acbdc08eb74
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54735457"
---
# <a name="customizing-operations-overview"></a><span data-ttu-id="4dd66-102">自訂作業：總覽</span><span class="sxs-lookup"><span data-stu-id="4dd66-102">Customizing Operations: Overview</span></span>
<span data-ttu-id="4dd66-103">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 預設會根據對應產生動態 SQL，以便進行插入、更新和刪除作業。</span><span class="sxs-lookup"><span data-stu-id="4dd66-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL for insert, update, and delete operations based on mapping.</span></span> <span data-ttu-id="4dd66-104">但實際上，您通常會想加入自己的業務邏輯，為安全性、驗證等做準備。</span><span class="sxs-lookup"><span data-stu-id="4dd66-104">However, in practice you typically want to add your own business logic to provide for security, validation, and so forth.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="4dd66-105">用於自訂這些作業的技術包括下列項目。</span><span class="sxs-lookup"><span data-stu-id="4dd66-105">techniques for customizing these operations include the following.</span></span>  
  
## <a name="loading-options"></a><span data-ttu-id="4dd66-106">載入選項</span><span class="sxs-lookup"><span data-stu-id="4dd66-106">Loading Options</span></span>  
 <span data-ttu-id="4dd66-107">在查詢中，您可以控制在您連接至資料庫時要擷取多少與主要目標相關的資料。</span><span class="sxs-lookup"><span data-stu-id="4dd66-107">In your queries, you can control how much data related to your main target is retrieved when you connect to the database.</span></span> <span data-ttu-id="4dd66-108">這項功能大部分是使用 <xref:System.Data.Linq.DataLoadOptions> 來實作。</span><span class="sxs-lookup"><span data-stu-id="4dd66-108">This functionality is implemented largely by using <xref:System.Data.Linq.DataLoadOptions>.</span></span> <span data-ttu-id="4dd66-109">如需詳細資訊，請參閱 <<c0> [ 延後執行與立即載入](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)。</span><span class="sxs-lookup"><span data-stu-id="4dd66-109">For more information, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="partial-methods"></a><span data-ttu-id="4dd66-110">部分方法</span><span class="sxs-lookup"><span data-stu-id="4dd66-110">Partial Methods</span></span>  
 <span data-ttu-id="4dd66-111">在其預設對應中，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 提供了部分方法來協助您實作商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="4dd66-111">In its default mapping, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides partial methods to help you implement your business logic.</span></span> <span data-ttu-id="4dd66-112">如需詳細資訊，請參閱 <<c0> [ 新增商務邏輯所使用部分方法](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="4dd66-112">For more information, see [Adding Business Logic By Using Partial Methods](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md).</span></span>  
  
## <a name="stored-procedures-and-user-defined-functions"></a><span data-ttu-id="4dd66-113">預存程序和使用者定義的函式</span><span class="sxs-lookup"><span data-stu-id="4dd66-113">Stored Procedures and User-Defined Functions</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="4dd66-114">支援使用預存程序和使用者定義函式。</span><span class="sxs-lookup"><span data-stu-id="4dd66-114">supports the use of stored procedures and user-defined functions.</span></span> <span data-ttu-id="4dd66-115">預存程序時常用於自訂作業。</span><span class="sxs-lookup"><span data-stu-id="4dd66-115">Stored procedures are frequently used to customize operations.</span></span> <span data-ttu-id="4dd66-116">如需詳細資訊，請參閱[預存程序](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="4dd66-116">For more information, see [Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dd66-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4dd66-117">See also</span></span>
- [<span data-ttu-id="4dd66-118">自訂插入、更新和刪除作業</span><span class="sxs-lookup"><span data-stu-id="4dd66-118">Customizing Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
