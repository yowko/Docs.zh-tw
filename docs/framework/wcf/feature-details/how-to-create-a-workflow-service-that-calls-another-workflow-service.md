---
title: HOW TO：建立會呼叫其他工作流程服務的工作流程服務
ms.date: 03/30/2017
ms.assetid: 99b3ee3e-aeb7-4e6f-8321-60fe6140eb67
ms.openlocfilehash: fda5a7286c3d20c7cdc2093e58bfe3fbdcf1d1c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-workflow-service-that-calls-another-workflow-service"></a>HOW TO：建立會呼叫其他工作流程服務的工作流程服務
有時工作流程服務需要從另一個工作流程服務取得資訊。  本主題示範如何從另一個工作流程服務呼叫某個工作流程服務。 在本主題中，我們會建立兩個工作流程服務，其中一個服務的方法會反轉輸入字串，而另一個服務則會在反轉使用第一個服務的字串之後，將輸入字串轉換成大寫。  
  
### <a name="to-create-the-reverser-workflow-service"></a>若要建立 Reverser 工作流程服務  
  
1.  以系統管理員身分執行 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]。  
  
2.  選取**檔案**，**新專案**。 在下**工作流程**節點**已安裝的範本**窗格中，選取**WCF 工作流程服務應用程式**。 將方案命名`NestedServices`，然後按一下 **確定**。  
  
3.  在下**伺服器**，請確定**使用本機 IIS Web 伺服器**已選取。 按一下**建立虛擬目錄**。 按一下**確定**對話方塊方塊，指出已成功建立虛擬目錄中。  
  
4.  在 [方案總管] 中，將 Service1.xamlx 重新命名以`StringReverserService.xamlx`。  
  
5.  在**專案屬性**新專案的頁面上，按一下**Web**  索引標籤。設定**起始動作**至**特定頁面**，並選取 StringReverserService.xamlx 當做起始頁面。  
  
6.  在設計工具中開啟 StringReverserService.xamlx 並刪除現有的 `ReceiveRequest` 和 `SendReply` 活動，然後將 `ReceiveAndSendReply` 活動拖曳到現有的序列活動中。  
  
    1.  設定**OperationName**為 ReverseString。  
  
    2.  設定**ServiceContractName**  設定為 IReverseString。  
  
    3.  選取**CanCreateInstance**核取方塊。  
  
7.  選取**SequentialService**活動，然後再按一下**變數**設計工具底部的索引標籤。 建立兩個新的變數，其名稱分別是 String 型別的 StringToReverse 和 ReversedStringToReturn。  
  
8.  按一下**定義**中連結**接收**活動。 按一下**參數**，並建立名為 InputString 會指派給 StringToReverse 的 String 型別參數。  
  
9. 按一下**定義**中連結**SendReplyToReceive**活動。 按一下**參數**，並建立名為 ReversedString String 型別，指派給 ReversedStringToReturn 參數。  
  
10. 若要實作此服務的邏輯，請在名為 StringLibrary 的專案中建立新的類別。  將此類別定義替換成下列程式碼。  
  
    ```  
    public class StringLibrary  
        {  
            public static String ReverseString(string StringToReverse)  
            {  
                char[] charArray = StringToReverse.ToCharArray();  
                Array.Reverse(charArray);  
                return new String(charArray);  
            }  
        }  
    ```  
  
11. 若要呼叫輸入上的 ReverseString 方法，將拖曳**InvokeMethod**活動從 [工具箱] 之間的空格**接收**和**SendReply**活動。 將活動的屬性設定如下：  
  
    1.  **MethodName**: ReverseString  
  
    2.  **結果**: ReversedStringToReturn  
  
    3.  **參數**： 建立新的參數與**方向**為 In，**類型**的字串，與**值**為 StringToReverse。  
  
    4.  **TargetType**: NestedServices.StringLibrary  
  
12. 按 F5 測試服務。 在出現的 WCF 測試用戶端中，按兩下 ReverseString() 方法。 在要求窗格中，輸入`Sample`，針對 InputString 參數的值。 按一下**叫用**。 此服務應該會傳回 "elpmaS"。  
  
### <a name="to-create-the-uppercaser-workflow-service"></a>若要建立 UpperCaser 工作流程服務  
  
1.  以滑鼠右鍵按一下 NestedServices 專案，然後選取**新增**，**新項目**。 在**工作流程**節點中，選取**WCF Workflow Service**，並為新的服務名稱`UpperCaserService`。 按一下 [加入] 。 這樣應該會將名為 UpperCaserService.xamlx 的新工作流程服務加入至專案中。  
  
2.  在設計工具中開啟 UpperCaserService.xamlx 並刪除現有**ReceiveRequest**和`SendReply`活動，然後拖曳`ReceiveAndSendReply`到現有的序列活動的活動。  
  
    1.  設定**OperationName**為 UpperCaseString。  
  
    2.  設定**ServiceContractName**  設定為 IUpperCaseString。  
  
    3.  選取**CanCreateInstance**核取方塊。  
  
3.  選取 [sequentialservice] 活動，然後再按一下**變數**設計工具底部的索引標籤。 建立三個新的變數，其名稱分別是 String 型別的 StringToUpper、StringToReverse 和 StringToReturn。  
  
4.  按一下**定義**中連結**接收**活動。 按一下**參數**，並建立名為 InputString 指派給 StringToUpper String 型別參數。  
  
5.  按一下**定義**中連結**SendReplyToReceive**活動。 按一下**參數**，並建立名為 ModifiedString String 型別，指派給 StringToReturn 參數。  
  
6.  若要實作此服務的邏輯，請使用下列程式碼在 StringLibrary 類別中建立新的方法。  
  
    ```  
    public static String UpperCaseString(string StringToUpperCase)  
    {  
         return StringToUpperCase.ToUpper();  
  
    }  
    ```  
  
7.  若要呼叫輸入上的 UpperCaseString 方法，將拖曳**InvokeMethod**活動從 [工具箱] 之間的空格**接收**和**SendReply**活動。 將活動的屬性設定如下：  
  
    1.  **MethodName**: UpperCaseString  
  
    2.  **結果**: StringToReverse  
  
    3.  **參數**： 建立新的參數與**方向**為 In，**類型**的字串，與**值**為 StringToUpper。  
  
    4.  **TargetType**: NestedServices.StringLibrary  
  
8.  現在我們要針對修改的字串呼叫第一個服務。 以滑鼠右鍵按一下專案，然後選取**加入服務參考**。 加入在服務的服務參考http://localhost/NestedServices/StringReverserService.xamlx和建置專案來建立自訂的活動，以便存取第一個 Web 服務。  
  
9. 之間拖曳到工作流程的新活動的執行個體**InvokeMethod**活動和**SendReplyToReceive**活動。 將 StringToReverse 變數指派給新活動的 InputString 屬性，並將 StringToReturn 變數指派給 StringToReturn 屬性。  
  
10. 開啟 NestedServices 專案的 屬性 頁面並變更**特定頁面**中**Web**為 UpperCaserService.xamlx 索引標籤。  
  
11. 按 F5 測試服務。 在出現的 WCF 測試用戶端中，按兩下 ReverseString() 方法。 在要求窗格中，輸入`Sample`，針對 InputString 參數的值。 按一下**叫用**。 此服務應該會傳回 "ELPMAS"。  
  
### <a name="to-create-a-client-to-call-the-services"></a>若要建立用戶端來呼叫服務  
  
1.  將名為 Client 的新主控台應用程式專案加入至方案中。  
  
2.  以滑鼠右鍵按一下 用戶端專案，然後選取**加入服務參考**。 在出現的視窗中，按一下**探索**。 選取 StringReverserService.xamlx 並輸入 ReverseService 當做命名空間。  按一下 [確定 **Deploying Office Solutions**]。  
  
3.  用下列程式碼取代 Program.cs 中的 Main 方法。  
  
    ```  
    static void Main(string[] args)  
    {  
        Console.Write("Input string to process:");  
        String input = Console.ReadLine();  
        var service = new ReverseService.ReverseStringClient();  
        Console.WriteLine("Output from service: {0}", service.ReverseString(input));  
        Console.ReadKey();  
    }  
    ```
