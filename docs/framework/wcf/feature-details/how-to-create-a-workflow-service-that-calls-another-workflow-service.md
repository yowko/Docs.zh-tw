---
title: "HOW TO：建立會呼叫其他工作流程服務的工作流程服務 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 99b3ee3e-aeb7-4e6f-8321-60fe6140eb67
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# HOW TO：建立會呼叫其他工作流程服務的工作流程服務
有時工作流程服務需要從另一個工作流程服務取得資訊。本主題示範如何從另一個工作流程服務呼叫某個工作流程服務。在本主題中，我們會建立兩個工作流程服務，其中一個服務的方法會反轉輸入字串，而另一個服務則會在反轉使用第一個服務的字串之後，將輸入字串轉換成大寫。  
  
### 若要建立 Reverser 工作流程服務  
  
1.  以系統管理員身分執行 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]。  
  
2.  選取 \[**檔案**\]、\[**新增專案**\]。在 \[**已安裝的範本**\] 窗格中的 \[**工作流程**\] 節點底下，選取 \[**WCF 工作流程服務應用程式**\]。將方案命名為 `NestedServices`，然後按一下 \[**確定**\]。  
  
3.  在 \[**伺服器**\] 底下，確定已選取 \[**使用本機 IIS Web 伺服器**\]。按一下 \[**建立虛擬目錄**\]。在陳述虛擬目錄已經建立成功的對話方塊中，按一下 \[**確定**\]。  
  
4.  在 \[方案總管\] 中，將 Service1.xamlx 重新命名為 `StringReverserService.xamlx`。  
  
5.  在新專案的 \[**專案屬性**\] 頁面上，按一下 \[**Web**\] 索引標籤。將 \[**起始動作**\] 設定為 \[**指定頁**\]，並選取 StringReverserService.xamlx 當做起始頁面。  
  
6.  在設計工具中開啟 StringReverserService.xamlx 並刪除現有的 `ReceiveRequest` 和 `SendReply` 活動，然後將 `ReceiveAndSendReply` 活動拖曳到現有的序列活動中。  
  
    1.  將 \[**OperationName**\] 設定為 ReverseString。  
  
    2.  將 \[**ServiceContractName**\] 設定為 IReverseString。  
  
    3.  選取 \[**CanCreateInstance**\] 核取方塊。  
  
7.  選取 \[**SequentialService**\] 活動，然後按一下設計工具底部的 \[**變數**\] 索引標籤。建立兩個新的變數，其名稱分別是 String 型別的 StringToReverse 和 ReversedStringToReturn。  
  
8.  在 **Receive** 活動中按一下 \[**定義**\] 連結。按一下 \[**參數**\] 並建立名為 InputString 且型別為 String 的參數 \(該參數會指派給 StringToReverse\)。  
  
9. 在 **SendReplyToReceive** 活動中按一下 \[**定義**\] 連結。按一下 \[**參數**\] 並建立名為 ReversedString 且型別為 String 的參數 \(該參數指派給 ReversedStringToReturn\)。  
  
10. 若要實作此服務的邏輯，請在名為 StringLibrary 的專案中建立新的類別。將此類別定義替換成下列程式碼。  
  
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
  
11. 若要呼叫輸入上的 ReverseString 方法，請將工具箱中的 **InvokeMethod** 活動拖曳到 **Receive** 與 **SendReply** 活動之間的空格。將活動的屬性設定如下：  
  
    1.  **MethodName**：ReverseString  
  
    2.  **結果**：ReversedStringToReturn  
  
    3.  **參數**：建立以下的新參數：\[**方向**\] 為 In，\[**型別**\] 為 String 且 \[**值**\] 為 StringToReverse。  
  
    4.  **TargetType**：NestedServices.StringLibrary  
  
12. 按 F5 測試服務。在出現的 WCF 測試用戶端中，按兩下 ReverseString\(\) 方法。在 \[要求\] 窗格中，針對 InputString 參數的值輸入 `Sample`。按一下 \[**叫用**\]。此服務應該會傳回 "elpmaS"。  
  
### 若要建立 UpperCaser 工作流程服務  
  
1.  以滑鼠右鍵按一下 NestedServices 專案，並選取 \[**新增**\]、\[**新增項目**\]。在 \[**工作流程**\] 節點中，選取 \[**WCF 工作流程服務**\]，並將新的服務命名為 `UpperCaserService`。按一下 \[**加入**\]。這樣應該會將名為 UpperCaserService.xamlx 的新工作流程服務加入至專案中。  
  
2.  在設計工具中開啟 UpperCaserService.xamlx 並刪除現有的 **ReceiveRequest** 和 `SendReply` 活動，然後將 `ReceiveAndSendReply` 活動拖曳到現有的序列活動中。  
  
    1.  將 \[**OperationName**\] 設定為 UpperCaseString。  
  
    2.  將 \[**ServiceContractName**\] 設定為 IUpperCaseString。  
  
    3.  選取 \[**CanCreateInstance**\] 核取方塊。  
  
3.  選取 \[SequentialService\] 活動，然後按一下設計工具底部的 \[**變數**\] 索引標籤。建立三個新的變數，其名稱分別是 String 型別的 StringToUpper、StringToReverse 和 StringToReturn。  
  
4.  在 **Receive** 活動中按一下 \[**定義**\] 連結。按一下 \[**參數**\] 並建立名為 InputString 且型別為 String 的參數 \(該參數會指派給 StringToUpper\)。  
  
5.  在 **SendReplyToReceive** 活動中按一下 \[**定義**\] 連結。按一下 \[**參數**\] 並建立名為 ModifiedString 且型別為 String 的參數 \(該參數指派給 StringToReturn\)。  
  
6.  若要實作此服務的邏輯，請使用下列程式碼在 StringLibrary 類別中建立新的方法。  
  
    ```  
    public static String UpperCaseString(string StringToUpperCase)  
    {  
         return StringToUpperCase.ToUpper();  
  
    }  
  
    ```  
  
7.  若要呼叫輸入上的 UpperCaseString 方法，請將工具箱中的 **InvokeMethod** 活動拖曳到 **Receive** 與 **SendReply** 活動之間的空格。將活動的屬性設定如下：  
  
    1.  **MethodName**：UpperCaseString  
  
    2.  **結果**：StringToReverse  
  
    3.  **參數**：建立以下的新參數：\[**方向**\] 為 In，\[**型別**\] 為 String 且 \[**值**\] 為 StringToUpper。  
  
    4.  **TargetType**：NestedServices.StringLibrary  
  
8.  現在我們要針對修改的字串呼叫第一個服務。以滑鼠右鍵按一下專案，並選取 \[**加入服務參考**\]。加入位於 http:\/\/localhost\/NestedServices\/StringReverserService.xamlx 之服務的服務參考，並建置專案來建立自訂活動，以便存取第一個 Web 服務。  
  
9. 將新活動的執行個體拖曳到工作流程上，介於 **InvokeMethod** 活動與 **SendReplyToReceive** 活動之間。將 StringToReverse 變數指派給新活動的 InputString 屬性，並將 StringToReturn 變數指派給 StringToReturn 屬性。  
  
10. 開啟 NestedServices 專案的 \[屬性\] 頁面，並將 \[**Web**\] 索引標籤中的 \[**指定頁**\] 變更為 UpperCaserService.xamlx。  
  
11. 按 F5 測試服務。在出現的 WCF 測試用戶端中，按兩下 ReverseString\(\) 方法。在 \[要求\] 窗格中，針對 InputString 參數的值輸入 `Sample`。按一下 \[**叫用**\]。此服務應該會傳回 "ELPMAS"。  
  
### 若要建立用戶端來呼叫服務  
  
1.  將名為 Client 的新主控台應用程式專案加入至方案中。  
  
2.  以滑鼠右鍵按一下 Client 專案，然後選取 \[**加入服務參考**\]。在隨即出現的視窗中，按一下 \[**探索**\]。選取 StringReverserService.xamlx 並輸入 ReverseService 當做命名空間。按一下 \[**確定**\]。  
  
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