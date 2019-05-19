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
# <a name="linq-to-sql-n-tier-with-aspnet"></a>LINQ to SQL 多層式架構與 ASP.NET
使用的 ASP.NET 應用程式中[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]，您使用<xref:System.Web.UI.WebControls.LinqDataSource>Web 伺服器控制項。 這個控制項負責大多數的必要邏輯，以查詢 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]、將資料傳遞至瀏覽器、擷取資料以及提交到 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> ，後者接著會更新資料庫。 您只要在標記中設定控制項，該控制項就會負責 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 與瀏覽器之間的所有資料傳輸作業。 因為這個控制項負責與展示層、 互動和[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]與資料層，您就能專注在 ASP.NET 多層式應用程式的通訊是在撰寫自訂商務邏輯的控制代碼。  
  
 如需詳細資訊`LINQDataSource`，請參閱 < [LinqDataSource Web Server Control Overview](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))。  
  
## <a name="see-also"></a>另請參閱

- [使用 LINQ to SQL 的多層式架構和遠端應用程式](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)
