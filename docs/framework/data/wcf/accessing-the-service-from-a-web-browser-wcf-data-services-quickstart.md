---
title: 從 Web 瀏覽器存取服務 (WCF 資料服務快速入門)
ms.date: 03/30/2017
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
ms.openlocfilehash: eb7f1c97722b45a93c310fb8bcbdb42beece2553
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780538"
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a>從 Web 瀏覽器存取服務 (WCF 資料服務快速入門)

這是 WCF Data Services 快速入門的第二項工作。 在這項工作中，您會從 Visual Studio 啟動 WCF Data Services，並選擇性地停用網頁瀏覽器中的摘要讀取功能。 接著，您可以透過 Web 瀏覽器將 HTTP GET 要求提交至已公開的資源，以抓取服務定義檔以及存取資料服務資源。

> [!NOTE]
> 根據預設，Visual Studio 會在您的電腦上自動指派連接埠號碼給 `localhost` URI。 這項工作會在 URI 範例中使用連接埠號碼 `12345`。 如需如何在 Visual Studio 專案中設定特定埠號碼的詳細資訊，請參閱[建立資料服務](creating-the-data-service.md)。

## <a name="to-request-the-default-service-document-by-using-internet-explorer"></a>若要使用 Internet Explorer 要求預設服務文件

1. 在 Internet Explorer 中，從 [**工具**] 功能表選取 [**網際網路選項**]，按一下 [**內容**] 索引標籤，按一下 [**設定**]，然後清除 [**開啟摘要查看**]。

     這樣可以確保摘要讀取功能已停用。 如果未停用此功能，Web 瀏覽器會將傳回的 AtomPub 編碼文件視為 XML 摘要，而不會顯示原始的 XML 資料。

    > [!NOTE]
    > 如果您的瀏覽器無法將摘要顯示為原始的 XML 資料，您應該仍然可以將摘要檢視為頁面的原始程式碼。

2. 在 Visual Studio 中，按**F5**鍵以開始對應用程式進行偵錯工具。

3. 開啟本機電腦上的 Web 瀏覽器。 在位址列中輸入下列 URI：

    ```
    http://localhost:12345/northwind.svc
    ```

     這樣會傳回預設的服務文件，其中包含此資料服務所公開的實體集清單。

## <a name="to-access-entity-set-resources-from-a-web-browser"></a>從 Web 瀏覽器存取實體集資源

1. 在 Web 瀏覽器的位址列中輸入下列 URI：

    ```
    http://localhost:12345/northwind.svc/Customers
    ```

     這樣會傳回 Northwind 範例資料庫中的所有客戶。

2. 在 Web 瀏覽器的位址列中輸入下列 URI：

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')
    ```

     這樣會傳回特定客戶 `ALFKI` 的實體執行個體。

3. 在 Web 瀏覽器的位址列中輸入下列 URI：

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders
    ```

     這樣會周遊客戶與訂單之間的關聯性，傳回特定客戶 `ALFKI` 的所有訂單。

4. 在 Web 瀏覽器的位址列中輸入下列 URI：

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643
    ```

     這樣會篩選屬於特定客戶 `ALFKI` 的訂單，因此僅根據所提供的 `OrderID` 值傳回特定訂單。

## <a name="next-steps"></a>後續步驟

您已成功從網頁瀏覽器存取 WCF Data Services，並將 HTTP GET 要求發出至指定的資源。 Web 瀏覽器可讓您輕鬆地實驗要求的定址語法並檢視結果。 不過，此方法通常並不適用於存取實際執行資料服務。 一般而言，應用程式會透過應用程式碼或指令碼語言與資料服務互動。 接下來，您將建立使用用戶端程式庫的用戶端應用程式，將資料服務資源視為 Common Language Runtime (CLR) 物件來加以存取：

> [!div class="nextstepaction"]
> [建立 .NET Framework 用戶端應用程式](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

## <a name="see-also"></a>另請參閱

- [存取資料服務資源](accessing-data-service-resources-wcf-data-services.md)
