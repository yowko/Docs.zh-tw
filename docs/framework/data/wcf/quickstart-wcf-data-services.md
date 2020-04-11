---
title: 快速入門 (WCF 資料服務)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: f945d33a4fc789b3c73c1c80040fc8527301758b
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121218"
---
# <a name="quickstart-wcf-data-services"></a>快速入門 (WCF 資料服務)

此快速入門可説明您通過一系列支援[入門](getting-started-with-wcf-data-services.md)主題的任務熟悉 WCF 數據服務和開放數據協定 (OData)。

## <a name="what-youll-learn"></a>您將學到什麼

此快速入門中的第一個任務演示如何創建數據服務以公開來自北風示例資料庫的 OData 源。 在後面的主題中,您將使用 Web 瀏覽器訪問 OData 源,還可以建立一個 Windows 演示文稿基礎 (WPF) 用戶端應用程式,該應用程式使用用戶端庫使用 OData 源。

## <a name="prerequisites"></a>Prerequisites

要完成此快速入門,請安裝以下元件:

- Visual Studio

- SQL 伺服器的實例。 這包括 SQL Server Express,它包含在 Visual Studio 2015 的預設安裝中,或作為 Visual Studio 2017 或更高版本中**的數據儲存和處理**工作負載的一部分。

- Northwind 範例資料庫。 要安裝資料庫,請從北風執行 Transact-SQL 文稿[,並為 Microsoft SQL Server 執行 pubs 範例資料庫](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)。

## <a name="wcf-data-services-quickstart-tasks"></a>WCF 資料服務快速啟動工作

 [建立資料服務](creating-the-data-service.md)

 定義 ADO.NET 應用程式、定義資料模型、建立資料服務，並且啟用資源存取。

 [從網頁瀏覽器存取服務](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 從 Visual Studio 啟動服務，然後透過 Web 瀏覽器將 HTTP GET 要求提交至公開的摘要，以存取該服務。

 [建立 .NET 框架客戶端應用程式](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 創建 WPF 應用以使用 OData 源、將資料綁定到 Windows 控制件、更改繫結項的資料,然後將更改發送回資料服務。

> [!NOTE]
> 專案檔從已完成版本的快速啟動可以從[GitHub](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))下載。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [開始快速入門](creating-the-data-service.md)

## <a name="see-also"></a>另請參閱

- [ADO.NET Entity Framework](../adonet/ef/index.md)
