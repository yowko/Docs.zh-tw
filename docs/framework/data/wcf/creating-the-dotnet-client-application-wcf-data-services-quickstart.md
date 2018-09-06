---
title: 建立 .NET Framework 用戶端應用程式 (WCF 資料服務快速入門)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
ms.openlocfilehash: 86ded7351d435b3a7077f0354d8a923b33a3f2b6
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43854953"
---
# <a name="creating-the-net-framework-client-application-wcf-data-services-quickstart"></a>建立 .NET Framework 用戶端應用程式 (WCF 資料服務快速入門)

這是在 WCF Data Services 快速入門的最後一項工作。 在這個工作中，您會新增至方案的主控台應用程式，請將參考加入[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]饋送到這個新的用戶端應用程式，以及存取 OData 摘要的用戶端應用程式，利用已產生的用戶端資料服務類別和用戶端程式庫.

> [!NOTE]
> 不需要 .NET Framework 架構的用戶端應用程式也可存取資料摘要。 資料服務可以存取任何取用 OData 摘要的應用程式元件。 如需詳細資訊，請參閱 <<c0> [ 用戶端應用程式中使用的資料服務](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md)。

## <a name="to-create-the-client-application-by-using-visual-studio"></a>若要使用 Visual Studio 建立用戶端應用程式

1.  中**方案總管**，以滑鼠右鍵按一下方案，按一下**新增**，然後按一下 **新專案**。

2.  在左窗格中，選取**已安裝**> [**Visual C#** 或是**Visual Basic**] > **Windows Desktop**，然後選取  **WPF 應用程式**範本。

3.  請輸入`NorthwindClient`做為專案名稱，然後按一下 **[確定]**。

4.  開啟 MainWindow.xaml 檔案，並以下列程式碼取代 XAML 程式碼：

     [!code-xaml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml#window1xaml)]

## <a name="to-add-a-data-service-reference-to-the-project"></a>若要將資料服務參考加入至專案

1.  在 **方案總管 中**，以滑鼠右鍵按一下 NorthwindClient 專案，按一下 **新增** > **服務參考**，然後按一下 **探索**.

     這會顯示您在第一個工作中建立的 Northwind 資料服務。

2.  在 **命名空間**文字方塊中，輸入`Northwind`，然後按一下**確定**。

     這會將新的程式碼檔案加入至專案中，此專案包含的資料類別可用來存取做為物件的資料服務資源，並與之進行互動。 在命名空間 `NorthwindClient.Northwind` 中建立資料類別。

## <a name="to-access-data-service-data-in-the-wpf-application"></a>在 WPF 應用程式中存取資料服務的資料

1.  在**方案總管**下方**NorthwindClient**，以滑鼠右鍵按一下專案，然後按一下**加入參考**。

2.  在 [**加入參考**] 對話方塊中，按一下 **.NET**索引標籤上，選取 System.Data.Services.Client.dll 組件，然後按一下 **[確定]**。

3. 在**方案總管**下方**NorthwindClient**，開啟 MainWindow.xaml 檔案的字碼頁，並新增下列`using`陳述式 (`Imports` Visual Basic 中)。

     [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#using)]
     [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#using)]

3.  插入下列查詢資料服務的程式碼，並將 <xref:System.Data.Services.Client.DataServiceCollection%601> 的結果繫結到 `MainWindow` 類別裡：

    > [!NOTE]
    > 您必須用裝載 Northwind 資料服務之執行個體的伺服器及連接埠來取代主機名稱 `localhost:12345`。

     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#querycode)]

4.  將下列儲存變更的程式碼插入 `MainWindow` 類別中：

     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#savechanges)]

## <a name="to-build-and-run-the-northwindclient-application"></a>建置和執行 NorthwindClient 應用程式

1.  在 **方案總管**，以滑鼠右鍵按一下 NorthwindClient 專案，然後選取**設定為啟始專案**。

2.  按下**F5**啟動應用程式。

     如此會建置方案，並啟動用戶端應用程式。 從服務要求資料，並顯示在主控台中。

3.  編輯中的值**Quantity**資料行的資料格，然後按一下**儲存**。

     資料服務的變更會被儲存。

    > [!NOTE]
    > 此版本的 NorthwindClient 應用程式不支援新增及刪除實體。

## <a name="next-steps"></a>後續步驟

您已成功建立存取的範例 Northwind OData 摘要的用戶端應用程式。 您也已經完成的 WCF Data Services 快速入門 ！

如需存取 OData 摘要[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]應用程式，請參閱 < [WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)。

## <a name="see-also"></a>另請參閱

- [快速入門](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
- [資源](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)
