---
title: HOW TO：搭配訊息活動建立工作流程服務
ms.date: 03/30/2017
ms.assetid: 53d094e2-6901-4aa1-88b8-024b27ccf78b
ms.openlocfilehash: 83e96a91348cd8f703801252109bd474df58a679
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2019
ms.locfileid: "58466201"
---
# <a name="how-to-create-a-workflow-service-with-messaging-activities"></a>HOW TO：搭配訊息活動建立工作流程服務
本主題描述如何使用訊息活動建立簡單的工作流程服務。 本主題的重點在於建立工作流程服務的機制，而該服務主要包含的便是訊息活動。 在真實世界的服務中，工作流程包含許多其他活動。 服務會實作一項稱為 Echo 的作業，該作業會使用字串並將字串傳回呼叫端。 本主題即為兩個主題的第一個。 下一個主題[How To:服務從工作流程應用程式存取](../../../../docs/framework/wcf/feature-details/how-to-access-a-service-from-a-workflow-application.md)討論如何建立工作流程應用程式，可以呼叫此主題中所建立的服務。  
  
### <a name="to-create-a-workflow-service-project"></a>若要建立工作流程服務專案  
  
1.  啟動 Visual Studio 2012。  
  
2.  按一下 [**檔案**功能表上，選取**新增**，然後**專案**以顯示**新增專案] 對話方塊**。 選取**工作流程**從清單中已安裝的範本並**WCF 工作流程服務應用程式**從專案類型清單。 將專案命名為`MyWFService`並使用預設位置，如下圖所示。  
  
     按一下 [ **[確定]** 按鈕以關閉**新增專案] 對話方塊**。  
  
3.  建立專案後，會在設計工具中開啟 Service1.xamlx 檔案，如下圖所示。  
  
     ![螢幕擷取畫面會顯示在設計工具中開啟 Service1.xamlx 檔案。](./media/how-to-create-a-workflow-service-with-messaging-activities/default-workflow-service.jpg)  
  
     以滑鼠右鍵按一下 標示為 活動**循序服務**，然後選取**刪除**。  
  
### <a name="to-implement-the-workflow-service"></a>若要實作工作流程服務  
  
1.  選取 **工具箱**来顯示工具箱，然後按一下圖釘，讓視窗保持開啟的畫面左側的索引標籤。 依序展開**Messaging**來顯示訊息活動和訊息活動範本，如下圖所示的工具箱 的區段。  
  
     ![螢幕擷取畫面顯示工具箱 與 傳訊 區段展開。](./media/how-to-create-a-workflow-service-with-messaging-activities/toolbox-messaging-section.jpg)  
  
2.  將拖放**ReceiveAndSendReply**工作流程設計工具的範本。 這會建立<xref:System.Activities.Statements.Sequence>活動，具有**接收**活動，隨後<xref:System.ServiceModel.Activities.SendReply>活動，如下圖所示。  
  
     ![如果螢幕擷取畫面顯示 ReceiveAndSendReply 範本。](./media/how-to-create-a-workflow-service-with-messaging-activities/receiveandsendreply-template.jpg)  
  
     注意，<xref:System.ServiceModel.Activities.SendReply> 活動的 <xref:System.ServiceModel.Activities.SendReply.Request%2A> 屬性會設為 `Receive`，也就是 <xref:System.ServiceModel.Activities.Receive> 活動所回覆之 <xref:System.ServiceModel.Activities.SendReply> 活動的名稱。  
  
3.  在 <xref:System.ServiceModel.Activities.Receive>活動型別`Echo`標示為文字方塊**OperationName**。 這樣做會定義服務所實作之作業的名稱。  
  
     ![如果螢幕擷取畫面顯示如何指定作業名稱。](./media/how-to-create-a-workflow-service-with-messaging-activities/define-operation-name.jpg)  
  
4.  具有<xref:System.ServiceModel.Activities.Receive>活動選取，開啟 屬性 視窗如果未開啟，即可**檢視**功能表，然後選取**屬性 視窗**。 在 [**屬性] 視窗**向下捲動，直到您看到**CanCreateInstance**按一下核取方塊，如下圖所示。 這項設定可讓工作流程服務主機在接收訊息時建立新的服務執行個體 (如果需要的話)。  
  
     ![如果螢幕擷取畫面顯示 CanCreateInstance 屬性。](./media/how-to-create-a-workflow-service-with-messaging-activities/cancreateinstance-property.jpg)  
  
5.  選取 <xref:System.Activities.Statements.Sequence>活動，然後按一下**變數**在設計工具左下角的按鈕。 如此將會顯示變數編輯器。 按一下 **建立的變數**連結，可新增變數來儲存傳送作業的字串。 變數命名`msg`並將其**變數**輸入為字串，如下圖所示。  
  
     ![如果螢幕擷取畫面示範如何加入的變數。](./media/how-to-create-a-workflow-service-with-messaging-activities/add-variable-msg-string.jpg)  
  
     按一下 **變數**按鈕以關閉變數編輯器。  
  
6.  按一下 **定義...** 連結**內容**中的文字方塊<xref:System.ServiceModel.Activities.Receive>活動，以顯示**內容定義**對話方塊。 選取 **參數**選項按鈕，按一下**加入新的參數**連結，輸入`inMsg`中**名稱**文字方塊中，選取**字串**中**型別**下拉式清單方塊中，然後輸入`msg`中**指派給**文字方塊中，如下圖所示。  
  
     ![如果螢幕擷取畫面顯示如何加入內容參數。](./media/how-to-create-a-workflow-service-with-messaging-activities/adding-parameters-content.jpg)  
  
     這樣會指定 [接收] 活動接收字串參數，且該資料繫結至 `msg` 變數。 按一下  **確定**以關閉**內容定義**對話方塊。  
  
7.  按一下 **定義...** 連結**內容**方塊中<xref:System.ServiceModel.Activities.SendReply>活動，以顯示**內容定義**對話方塊。 選取 **參數**選項按鈕，按一下**加入新的參數**連結，輸入`outMsg`中**名稱**文字方塊中，選取**字串**中**型別**下拉式清單方塊中，並`msg`中**值**文字方塊中，如下圖所示。  
  
     ![如果螢幕擷取畫面示範如何加入 outMsg 參數。](./media/how-to-create-a-workflow-service-with-messaging-activities/outmsg-parameters-content.jpg)  
  
     這樣會指定 <xref:System.ServiceModel.Activities.SendReply> 活動傳送訊息或訊息合約型別，且該資料繫結至 `msg` 變數。 由於此為 <xref:System.ServiceModel.Activities.SendReply> 活動，代表 `msg` 中的資料是用來填入由活動傳回用戶端的訊息。 按一下  **確定**以關閉**內容定義**對話方塊。  
  
8.  儲存並建置方案，依序按一下**建置**功能表，然後選取**建置方案**。  
  
## <a name="configure-the-workflow-service-project"></a>設定工作流程服務專案。  
 工作流程執行服務已完成。 本節說明如何設定工作流程服務方案，讓裝載和執行更順利。 此方案是使用 ASP.NET 程式開發伺服器來裝載服務。  
  
#### <a name="to-set-project-start-up-options"></a>若要設定專案啟動選項  
  
1.  在 [**方案總管] 中**，以滑鼠右鍵按一下**MyWFService** ，然後選取**屬性**顯示**專案屬性**對話方塊。  
  
2.  選取**Web**索引標籤，然後選取**特定頁面**之下**起始動作**並輸入`Service1.xamlx`在文字方塊中，如下圖所示。  
  
     ![如果螢幕擷取畫面顯示 [專案屬性] 對話方塊。](./media/how-to-create-a-workflow-service-with-messaging-activities/project-properties-dialog.jpg)  
  
     這樣做會裝載在 ASP.NET 程式開發伺服器的 Service1.xamlx 中所定義的服務。  
  
3.  按 Ctrl+F5 啟動服務。 [ASP.NET 程式開發伺服器] 圖示會顯示在桌面的右下角，如下圖所示。  
  
     ![如果螢幕擷取畫面顯示的 ASP.NET 開發人員伺服器圖示。](./media/how-to-create-a-workflow-service-with-messaging-activities/asp-net-dev-server-icon.jpg)  
  
     此外，Internet Explorer 還會顯示該服務的 WCF 服務說明網頁。  
  
     ![如果螢幕擷取畫面顯示 WCF 服務說明頁面。](./media/how-to-create-a-workflow-service-with-messaging-activities/wcf-service-help-page.jpg)  
  
4.  繼續前往[How To:服務從工作流程應用程式存取](../../../../docs/framework/wcf/feature-details/how-to-access-a-service-from-a-workflow-application.md)主題，以建立工作流程用戶端可呼叫此服務。  
  
## <a name="see-also"></a>另請參閱
- [工作流程服務](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [裝載工作流程服務概觀](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)
- [傳訊活動](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
