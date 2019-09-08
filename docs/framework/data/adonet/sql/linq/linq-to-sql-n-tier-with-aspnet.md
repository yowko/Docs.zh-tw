---
title: LINQ to SQL 多層式架構與 ASP.NET
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: 1770d84053b57e05d1a4e41919a3eb4122dc73a3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793030"
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a>LINQ to SQL 多層式架構與 ASP.NET
在使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]的 ASP.NET 應用程式中，您<xref:System.Web.UI.WebControls.LinqDataSource>可以使用 Web 服務器控制項。 這個控制項負責大多數的必要邏輯，以查詢 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]、將資料傳遞至瀏覽器、擷取資料以及提交到 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> ，後者接著會更新資料庫。 您只要在標記中設定控制項，該控制項就會負責 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 與瀏覽器之間的所有資料傳輸作業。 由於此控制項會處理與展示層的互動，並[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]處理與資料層的通訊，因此 ASP.NET 多層式應用程式的主要焦點在於撰寫您的自訂商務邏輯。  
  
 如需的詳細`LINQDataSource`資訊，請參閱[LinqDataSource Web 服務器控制項總覽](https://docs.microsoft.com/previous-versions/aspnet/bb547113(v=vs.100))。  
  
## <a name="see-also"></a>另請參閱

- [使用 LINQ to SQL 的多層式架構和遠端應用程式](n-tier-and-remote-applications-with-linq-to-sql.md)
