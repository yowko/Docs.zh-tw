---
title: LINQ to SQL 多層式架構與 ASP.NET
ms.date: 03/30/2017
ms.assetid: f6cc863a-d6a6-4281-ba8b-197c01cf6c6f
ms.openlocfilehash: 1af7f0d78f16e25c1ae7bf563c6abfb3b77f6183
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559222"
---
# <a name="linq-to-sql-n-tier-with-aspnet"></a>LINQ to SQL 多層式架構與 ASP.NET
在使用的 ASP.NET 應用程式中 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ，您可以使用 <xref:System.Web.UI.WebControls.LinqDataSource> Web 服務器控制項。 控制項會處理查詢所需的大部分邏輯 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 、將資料傳遞至瀏覽器、取出資料，然後將它提交至， [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext> 然後更新資料庫。 您只要在標記中設定控制項，該控制項就會負責 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 與瀏覽器之間的所有資料傳輸作業。 因為此控制項會處理與展示層的互動，並 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 處理與資料層的通訊，所以 ASP.NET 多層式應用程式的主要重點在於撰寫您的自訂商務邏輯。  
  
 如需的詳細資訊 `LINQDataSource` ，請參閱 [LinqDataSource Web 服務器控制項總覽](/previous-versions/aspnet/bb547113(v=vs.100))。  
  
## <a name="see-also"></a>另請參閱

- [多層式架構和遠端應用程式以及 LINQ to SQL](n-tier-and-remote-applications-with-linq-to-sql.md)
