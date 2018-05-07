---
title: HOW TO：建立會取用現有服務合約的工作流程服務
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: 146b3bba3a880c780644eecd277827823793b5e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a>HOW TO：建立會取用現有服務合約的工作流程服務
[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 採用合約優先工作流程開發形式，可在 Web 服務和工作流程中提供更好的整合。 合約優先工作流程開發工具可讓您在 Code First 中設計合約。 此工具會自動在合約中的作業工具箱內產生活動範本。  
  
> [!NOTE]
>  本主題提供建立合約優先工作流程服務的逐步指示。 如需合約優先工作流程服務開發的詳細資訊，請參閱[合約第一個工作流程服務開發](../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md)。  
  
### <a name="creating-the-workflow-project"></a>建立工作流程專案  
  
1.  在 Visual Studio 中，選取**檔案**，**新專案**。 選取**WCF**節點下的**C#** 節點**範本**樹狀，並選取**WCF 工作流程服務應用程式**範本。  
  
2.  將新專案`ContractFirst`按一下**確定**。  
  
### <a name="creating-the-service-contract"></a>建立服務合約  
  
1.  中的專案上按一下滑鼠右鍵**方案總管 中**選取**新增**，**新項目...**. 選取**程式碼**節點的左側，而**類別**右邊的範本。 將新類別`IBookService`按一下**確定**。  
  
2.  在出現的程式碼視窗最上方，將 Using 陳述式加入到 `System.Servicemodel`。  
  
    ```  
    using System.ServiceModel;  
    ```  
  
3.  將範例類別定義變更為下列介面定義。  
  
    ```  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4.  建置專案時按**Ctrl + Shift + B**。  
  
### <a name="importing-the-service-contract"></a>匯入服務合約  
  
1.  中的專案上按一下滑鼠右鍵**方案總管 中**選取**匯入服務合約**。 在下**\<目前專案 >**，開啟所有的子節點並選取**IBookService**。 按一下 [確定 **Deploying Office Solutions**]。  
  
2.  隨即會開啟一個對話方塊，警告您作業已成功完成，且所產生的活動將會在您建置專案後出現在工具箱中。 按一下 [確定 **Deploying Office Solutions**]。  
  
3.  建置專案時按**Ctrl + Shift + B**，如此一來，匯入的活動將會出現在工具箱中。  
  
4.  在**方案總管 中**，開啟.service1.xamlx。 工作流程服務會出現在設計工具中。  
  
5.  選取**順序**活動。 在 [屬性] 視窗中，按一下 **...** 按鈕**ImplementedContract**屬性。 在**型別集合編輯器**視窗中，按一下 **類型**下拉式清單中，然後選取**瀏覽型別...** 項目。 在**瀏覽並選取.Net 型別**對話方塊下方**\<目前專案 >**，開啟所有的子節點並選取**IBookService**。 按一下 [確定 **Deploying Office Solutions**]。 在**型別集合編輯器**] 對話方塊中，按一下 [**確定**。  
  
6.  選取並刪除**ReceiveRequest**和**SendResponse**活動。  
  
7.  從工具箱 拖曳**Buy_ReceiveAndSendReply**和**Checkout_Receive**活動放置到**循序服務**活動。
