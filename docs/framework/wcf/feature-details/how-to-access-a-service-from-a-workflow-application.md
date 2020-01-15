---
title: HOW TO：存取來自工作流程應用程式的服務
ms.date: 03/30/2017
ms.assetid: 925ef8ea-5550-4c9d-bb7b-209e20c280ad
ms.openlocfilehash: c524dc07106f039d9dc6c17ee6fb966321b6da24
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964521"
---
# <a name="how-to-access-a-service-from-a-workflow-application"></a>HOW TO：存取來自工作流程應用程式的服務
本主題描述如何從工作流程主控台應用程式呼叫工作流程服務。 這取決於[如何：使用訊息活動建立工作流程服務](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)主題。 雖然本主題描述如何從工作流應用程式呼叫工作流程服務，但您可以使用相同的方法，從工作流程應用程式呼叫任何 Windows Communication Foundation （WCF）服務。

### <a name="create-a-workflow-console-application-project"></a>建立工作流程主控台應用程式專案

1. 啟動 Visual Studio 2012。

2. 載入您在[如何：使用訊息活動建立工作流程服務](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)主題中建立的 MyWFService 專案。

3. 以滑鼠右鍵按一下**方案總管**中的 [ **MyWFService** ] 方案，然後選取 [**加入**]、[**新增專案**]。 從專案類型清單中選取 [**已安裝的範本**和**工作流程主控台應用程式**] 中的 [**工作流程**]。 將專案命名為 MyWFClient，並且使用預設位置，如下圖所示。

     ![加入新的專案對話](./media/how-to-access-a-service-from-a-workflow-application/add-new-project-dialog.jpg)

     按一下 [**確定]** 按鈕，以關閉 [**加入新專案] 對話方塊**。

4. 建立專案之後，Workflow1.xaml 檔會在設計工具中開啟。 按一下 [**工具箱**] 索引標籤以開啟 [工具箱] （如果尚未開啟），然後按一下圖釘讓 [工具箱] 視窗保持開啟。

5. 按**Ctrl**+**F5**以建立並啟動服務。 ASP.NET 程式開發伺服器會如往常一般隨即啟動，而且 Internet Explorer 會顯示 WCF 說明網頁。 請記下這個網頁的 URI，因為您必須在下一個步驟中使用。

     ![顯示 WCF 說明頁面和 URI 的 IE](./media/how-to-access-a-service-from-a-workflow-application/ie-wcf-help-page-uri.jpg)

6. 以滑鼠右鍵按一下**方案總管**中的 [ **MyWFClient** ] 專案，然後選取 [**加入** > **服務參考**]。 按一下 [**探索**] 按鈕，在目前的解決方案中搜尋任何服務。 按一下 [服務] 清單中 Service1.xamlx 旁邊的三角形。 按一下 Service1 旁邊的三角形，即可列出 Service1 服務實作的合約。 展開 [**服務**] 清單中的 [ **Service1** ] 節點。 [動作] 清單中會顯示 Echo**作業**，如下圖所示。

     ![加入服務參考對話](./media/how-to-access-a-service-from-a-workflow-application/add-service-reference.jpg)

     保留預設的命名空間，然後按一下 **[確定]** 以關閉 [**加入服務參考**] 對話方塊。 此時會顯示下列對話方塊。

     ![加入服務參考通知對話方塊](./media/how-to-access-a-service-from-a-workflow-application/add-service-reference-dialog.jpg)

     按一下 **[確定**] 以關閉對話方塊。 接著，請按下 CTRL+SHIFT+B 建置方案。 請注意，在 [工具箱] 中，已新增一個新的區段，稱為**MyWFClient ServiceReference1。活動**。 展開此區段並注意已加入的 Echo 活動，如下圖所示。

     ![工具箱中的 Echo 活動](./media/how-to-access-a-service-from-a-workflow-application/echo-activity-toolbox.jpg)

7. 將 <xref:System.Activities.Statements.Sequence> 活動拖放至設計工具介面上。 它位於 [工具箱] 的 [**控制流程**] 區段底下。

8. 在焦點的 <xref:System.Activities.Statements.Sequence> 活動中，按一下 [**變數**] 連結，然後新增名為 `inString`的字串變數。 為變數指定預設值 `"Hello, world"`，以及名為 `outString` 的字串變數，如下圖所示。

     ![新增 inString 變數](./media/how-to-access-a-service-from-a-workflow-application/add-instring-variable.jpg)

9. 將**Echo**活動拖放到 <xref:System.Activities.Statements.Sequence>中。 在 [屬性] 視窗中，將 `inMsg` 引數系結至 `inString` 變數，並將 `outMsg` 引數系結至 `outString` 變數，如下圖所示。 這樣做會將 `inString` 變數的值傳遞至作業中，然後取得傳回值並放入 `outString` 變數。

     ![將引數繫結至變數](./media/how-to-access-a-service-from-a-workflow-application/bind-arguments-variables.jpg)

10. 將 [ **WriteLine** ] 活動拖放到 [ **Echo** ] 活動下方，以顯示服務呼叫所傳回的字串。 [ **WriteLine** ] 活動位於 [工具箱] 的 [**基本**] 節點中。 在 [ **writeline** ] 活動的文字方塊中輸入 `outString`，將 [ **writeline** ] 活動的 [ **Text** ] 引數系結至 `outString` 變數。 現在，工作流程的外觀應該如下圖所示。

     ![完整的用戶端工作流程](./media/how-to-access-a-service-from-a-workflow-application/complete-client-workflow.jpg)

11. 以滑鼠右鍵按一下 [MyWFService] 方案，然後選取 [**設定啟始專案**...]。選取 [**多個啟始專案**] 選項按鈕，然後針對 [**動作**] 資料行中的每個專案選取 [**啟動**]，如下圖所示。

     ![啟動專案選項](./media/how-to-access-a-service-from-a-workflow-application/startup-project-options.jpg)

12. 按下 Ctrl+F5，同時啟動服務與用戶端。 ASP.NET 程式開發伺服器裝載服務時，Internet Explorer 會顯示 WCF 說明頁面，而用戶端工作流程應用程式會在主控台視窗中啟動，並顯示從服務傳回的字串（"Hello，world"）。

## <a name="see-also"></a>請參閱

- [工作流程服務](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [如何：使用傳訊活動建立工作流程服務](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [從 Web 專案中的工作流程使用 WCF 服務](https://docs.microsoft.com/archive/blogs/endpoint/how-to-consume-a-wcf-service-from-a-wf4-workflow)
