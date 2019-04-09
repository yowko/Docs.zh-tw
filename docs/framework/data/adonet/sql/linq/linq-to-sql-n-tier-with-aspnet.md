---
title: LINQ to SQL 多層式架構與 ASP.NET
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: 80c12d1c9f290657a6e005063d9cc77a17354abd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103724"
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a><span data-ttu-id="69973-102">LINQ to SQL 多層式架構與 ASP.NET</span><span class="sxs-lookup"><span data-stu-id="69973-102">LINQ to SQL N-Tier with ASP.NET</span></span>
<span data-ttu-id="69973-103">在使用 [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] 的 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]應用程式中，您可以使用 <xref:System.Web.UI.WebControls.LinqDataSource> Web 伺服器控制項。</span><span class="sxs-lookup"><span data-stu-id="69973-103">In [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] applications that use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you use the <xref:System.Web.UI.WebControls.LinqDataSource> Web server control.</span></span> <span data-ttu-id="69973-104">這個控制項負責大多數的必要邏輯，以查詢 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]、將資料傳遞至瀏覽器、擷取資料以及提交到 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> ，後者接著會更新資料庫。</span><span class="sxs-lookup"><span data-stu-id="69973-104">The control handles most of the logic that it must have to query against [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], pass the data to the browser, retrieve it, and submit it to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> which then updates the database.</span></span> <span data-ttu-id="69973-105">您只要在標記中設定控制項，該控制項就會負責 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 與瀏覽器之間的所有資料傳輸作業。</span><span class="sxs-lookup"><span data-stu-id="69973-105">You just configure the control in the markup, and the control handles all the data transfer between [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] and the browser.</span></span> <span data-ttu-id="69973-106">由於有這個控制項負責與展示層的互動，又有 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 負責與資料層溝通，您就能專注在 [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] 多層應用程式中撰寫自訂商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="69973-106">Because the control handles the interactions with the presentation tier, and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] handles the communication with the data tier, your main focus in [!INCLUDE[vstecasp](../../../../../../includes/vstecasp-md.md)] multitier applications is on writing your custom business logic.</span></span>  
  
 <span data-ttu-id="69973-107">如需詳細資訊`LINQDataSource`，請參閱 < [LinqDataSource Web Server Control Overview](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="69973-107">For more information about `LINQDataSource`, see [LinqDataSource Web Server Control Overview](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69973-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69973-108">See also</span></span>

- [<span data-ttu-id="69973-109">多層式架構和遠端應用程式以及 LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="69973-109">N-Tier and Remote Applications with LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
