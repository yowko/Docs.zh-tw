---
title: 建立 .NET Framework 用戶端應用程式 (WCF 資料服務快速入門)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
ms.openlocfilehash: 09981a7aee2db24d8464bbc7412b82a57ec8115b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="creating-the-net-framework-client-application-wcf-data-services-quickstart"></a>建立 .NET Framework 用戶端應用程式 (WCF 資料服務快速入門)
這是最後一項工作[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]快速入門。 在這項工作，您會加入至方案的主控台應用程式，請將參考加入[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]饋送到這個新的用戶端應用程式及存取[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]使用所產生的用戶端資料服務類別和用戶端從用戶端應用程式摘要程式庫。  
  
> [!NOTE]
>  不需要 .NET Framework 架構的用戶端應用程式也可存取資料摘要。 此資料服務可由取用 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要的任何應用程式元件所存取。 如需詳細資訊，請參閱[用戶端應用程式中使用資料服務](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md)。  
  
### <a name="to-create-the-client-application-by-using-visual-studio"></a>若要使用 Visual Studio 建立用戶端應用程式  
  
1.  在**方案總管] 中**，以滑鼠右鍵按一下方案，按一下**新增**，然後按一下 [**新專案**。  
  
2.  在**專案類型**，按一下  **Windows**，然後選取**WPF 應用程式**中**範本**窗格。  
  
3.  輸入`NorthwindClient`為專案名稱，然後按一下**確定**。  
  
4.  開啟 MainWindow.xaml 檔案，並以下列程式碼取代 XAML 程式碼：  
  
     [!code-xaml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml#window1xaml)]  
  
### <a name="to-add-a-data-service-reference-to-the-project"></a>若要將資料服務參考加入至專案  
  
1.  以滑鼠右鍵按一下 NorthwindClient 專案，請按一下**加入服務參考**，然後按一下 **探索**。  
  
     這會顯示您在第一個工作中建立的 Northwind 資料服務。  
  
2.  在**命名空間**文字方塊中，輸入`Northwind`，然後按一下 **確定**。  
  
     這會將新的程式碼檔案加入至專案中，此專案包含的資料類別可用來存取做為物件的資料服務資源，並與之進行互動。 在命名空間 `NorthwindClient.Northwind` 中建立資料類別。  
  
### <a name="to-access-data-service-data-in-the-wpf-application"></a>在 WPF 應用程式中存取資料服務的資料  
  
1.  在**方案總管 中**下**NorthwindClient**，以滑鼠右鍵按一下專案，然後按一下**加入參考**。  
  
2.  在 [加入參考] 對話方塊中，按一下 **.NET**索引標籤上，選取 System.Data.Services.Client.dll 組件，然後按一下**確定**。 在**方案總管 中**下**NorthwindClient**，開啟 MainWindow.xaml 檔案的字碼頁並加入下列`using`陳述式 (`Imports`在 Visual Basic 中)。  
  
     [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#using)]
     [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#using)]  
  
3.  插入下列查詢資料服務的程式碼，並將 <xref:System.Data.Services.Client.DataServiceCollection%601> 的結果繫結到 `MainWindow` 類別裡：  
  
    > [!NOTE]
    >  您必須用裝載 Northwind 資料服務之執行個體的伺服器及連接埠來取代主機名稱 `localhost:12345`。  
  
     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#querycode)]  
  
4.  將下列儲存變更的程式碼插入 `MainWindow` 類別中：  
  
     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart client/vb/window1.xaml.vb#savechanges)]  
  
### <a name="to-build-and-run-the-northwindclient-application"></a>建置和執行 NorthwindClient 應用程式  
  
1.  在**方案總管 中**，以滑鼠右鍵按一下 NorthwindClient 專案，然後選取**設定為啟始專案**。  
  
2.  請按 F5 啟動應用程式。  
  
     如此會建置方案，並啟動用戶端應用程式。 從服務要求資料，並顯示在主控台中。  
  
3.  編輯中的值**數量**資料行的資料格，然後按一下**儲存**。  
  
     資料服務的變更會被儲存。  
  
    > [!NOTE]
    >  此版本的 NorthwindClient 應用程式不支援新增及刪除實體。  
  
## <a name="next-steps"></a>後續步驟  
 您已成功建立存取範例 Northwind [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要的用戶端應用程式。 您也已經完成 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 快速入門。 如需有關存取[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]從摘要[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]應用程式，請參閱[WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)。  
  
## <a name="see-also"></a>另請參閱  
 [快速入門](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 [資源](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)
