---
title: LINQ to SQL 多層式架構與 ASP.NET
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: 85ead36d1d927084c11dca1bd73a192b16e4ab7b
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880759"
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a><span data-ttu-id="3c380-102">LINQ to SQL 多層式架構與 ASP.NET</span><span class="sxs-lookup"><span data-stu-id="3c380-102">LINQ to SQL N-Tier with ASP.NET</span></span>
<span data-ttu-id="3c380-103">使用的 ASP.NET 應用程式中[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]，您使用<xref:System.Web.UI.WebControls.LinqDataSource>Web 伺服器控制項。</span><span class="sxs-lookup"><span data-stu-id="3c380-103">In ASP.NET applications that use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you use the <xref:System.Web.UI.WebControls.LinqDataSource> Web server control.</span></span> <span data-ttu-id="3c380-104">這個控制項負責大多數的必要邏輯，以查詢 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]、將資料傳遞至瀏覽器、擷取資料以及提交到 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> ，後者接著會更新資料庫。</span><span class="sxs-lookup"><span data-stu-id="3c380-104">The control handles most of the logic that it must have to query against [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], pass the data to the browser, retrieve it, and submit it to the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> which then updates the database.</span></span> <span data-ttu-id="3c380-105">您只要在標記中設定控制項，該控制項就會負責 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 與瀏覽器之間的所有資料傳輸作業。</span><span class="sxs-lookup"><span data-stu-id="3c380-105">You just configure the control in the markup, and the control handles all the data transfer between [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] and the browser.</span></span> <span data-ttu-id="3c380-106">因為這個控制項負責與展示層、 互動和[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]與資料層，您就能專注在 ASP.NET 多層式應用程式的通訊是在撰寫自訂商務邏輯的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="3c380-106">Because the control handles the interactions with the presentation tier, and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] handles the communication with the data tier, your main focus in ASP.NET multitier applications is on writing your custom business logic.</span></span>  
  
 <span data-ttu-id="3c380-107">如需詳細資訊`LINQDataSource`，請參閱 < [LinqDataSource Web Server Control Overview](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="3c380-107">For more information about `LINQDataSource`, see [LinqDataSource Web Server Control Overview](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c380-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c380-108">See also</span></span>

- [<span data-ttu-id="3c380-109">使用 LINQ to SQL 的多層式架構和遠端應用程式</span><span class="sxs-lookup"><span data-stu-id="3c380-109">N-Tier and Remote Applications with LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
