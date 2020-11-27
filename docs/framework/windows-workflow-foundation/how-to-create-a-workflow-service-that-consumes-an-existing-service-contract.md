---
title: 作法：建立會取用現有服務合約的工作流程服務
ms.date: 03/30/2017
ms.assetid: 11d11b59-acc4-48bf-8e4b-e97b516aa0a9
ms.openlocfilehash: 05c59bde424049eb5bef8f8bd09c472b58eaa9ef
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248821"
---
# <a name="how-to-create-a-workflow-service-that-consumes-an-existing-service-contract"></a>作法：建立會取用現有服務合約的工作流程服務

.NET Framework 4.5 以合約優先工作流程開發的形式，在 web 服務與工作流程之間提供更好的整合。 合約優先工作流程開發工具可讓您在 Code First 中設計合約。 此工具會自動在合約中的作業工具箱內產生活動範本。  
  
> [!NOTE]
> 本主題提供建立合約優先工作流程服務的逐步指示。 如需有關合約優先工作流程服務開發的詳細資訊，請參閱 [合約優先工作流程服務開發](contract-first-workflow-service-development.md)。  
  
### <a name="creating-the-workflow-project"></a>建立工作流程專案  
  
1. 在 Visual Studio 中，選取 [檔案]、[新增專案]。 在 [**範本**] 樹狀結構中，選取 [ **c #** ] 節點底下的 [ **wcf** ] 節點，然後選取 [ **wcf Workflow Service 應用程式**] 範本。  
  
2. 將新專案命名為 `ContractFirst` ，然後按一下 **[確定]**。  
  
### <a name="creating-the-service-contract"></a>建立服務合約  
  
1. 以滑鼠右鍵按一下 **方案總管** 中的專案，然後選取 [ **加入**]、[ **新增專案 ...**]。 選取左側的 [程式 **代碼** ] 節點和右邊的 [ **類別** ] 範本。 將新類別命名為 `IBookService` ，然後按一下 **[確定]**。  
  
2. 在出現的程式碼視窗最上方，將 Using 陳述式加入到 `System.Servicemodel`。  
  
    ```csharp  
    using System.ServiceModel;  
    ```  
  
3. 將範例類別定義變更為下列介面定義。  
  
    ```csharp  
    [ServiceContract]  
        public interface IBookService  
        {  
            [OperationContract]  
            void Buy(string bookName);  
  
            [OperationContract(IsOneWay=true)]  
            void Checkout();  
        }  
    ```  
  
4. 按下 **Ctrl + Shift + B** 以建立專案。  
  
### <a name="importing-the-service-contract"></a>匯入服務合約  
  
1. 以滑鼠右鍵按一下 **方案總管** 中的專案，然後選取 [匯 **入服務合約**]。 在底下 **\<Current Project>** ，開啟所有子節點，然後選取 [ **[ibookservice**]。 按一下 [確定]。  
  
2. 隨即會開啟一個對話方塊，警告您作業已成功完成，且所產生的活動將會在您建置專案後出現在工具箱中。 按一下 [確定]。  
  
3. 按 **Ctrl + Shift + B** 來建立專案，讓匯入的活動會出現在 [工具箱] 中。  
  
4. 在 **方案總管** 中，開啟 Service1 service1.xamlx。 工作流程服務會出現在設計工具中。  
  
5. 選取 **序列** 活動。 在 [屬性視窗中，按一下 **...** 按鈕（ **ImplementedContract** 屬性）。 在出現的 [**型別集合編輯器**] 視窗中，按一下 [**類型**] 下拉式清單，然後選取 [**流覽類型 ...]** 。 項目。 在 [ **流覽並選取 .Net 類型** ] 對話方塊中，于底下 **\<Current Project>** 開啟 [所有子節點]，然後選取 [ **[ibookservice**]。 按一下 [確定]。 在 [ **型別集合編輯器** ] 對話方塊中，按一下 **[確定]**。  
  
6. 選取並刪除 **ReceiveRequest** 和 **SendResponse** 活動。  
  
7. 將 [ **Buy_ReceiveAndSendReply** ] 和 [ **Checkout_Receive** ] 活動從 [工具箱] 拖曳到 [ **順序服務** ] 活動上。
