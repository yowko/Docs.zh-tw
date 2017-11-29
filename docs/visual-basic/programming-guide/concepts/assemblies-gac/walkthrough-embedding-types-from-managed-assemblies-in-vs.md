---
title: "逐步解說： 在 Visual Studio (Visual Basic) 中內嵌 Managed 組件的類型"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56ed12ba-adff-4e9c-a668-7fcba80c4795
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4411b40d8ffbdf2b74c49152db675286d91b43ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-visual-basic"></a>逐步解說： 在 Visual Studio (Visual Basic) 中內嵌 Managed 組件的類型
若要內嵌來自強式名稱 Managed 組件的類型資訊，您可以鬆散地結合應用程式中的類型以確保版本獨立。 也就是說，您可以撰寫程式來使用 Managed 程式庫多個版本的類型，而不需重新編譯每個版本。  
  
 內嵌型別時，通常會搭配使用 COM Interop (例如從 Microsoft Office 使用 Automation 物件的應用程式)。 當您內嵌類型資訊時，可讓相同組建的程式使用不同電腦上版本各異的 Microsoft Office。 不過，您也可以搭配使用類型內嵌功能與完全受管理的解決方案。  
  
 您可以透過組件來內嵌具有下列特性的類型資訊：  
  
-   組件已公開至少一個公用介面。  
  
-   內嵌的介面已標註 `ComImport` 屬性和 `Guid` 屬性 (以及唯一 GUID)。  
  
-   您可以使用 `ImportedFromTypeLib` 屬性或 `PrimaryInteropAssembly` 屬性及組件層級 `Guid` 屬性，來標註組件  (根據預設，Visual Basic 專案範本包含組件層級`Guid`屬性。)  
  
 指定可內嵌的公用介面之後，您可以建立執行階段類別以實作這些介面。 接著，用戶端程式即會參考包含公用介面的組件，然後將參考的 `Embed Interop Types` 屬性設為 `True`，以在設計階段內嵌這些介面的類型資訊。 這相當於使用命令列編譯器，並使用 `/link` 編譯器選項來參考組件。 用戶端程式即可載入以這些介面為類型的執行階段物件執行個體。 如果您建立新版本的強式名稱執行階段組件，用戶端程式就不需要使用更新的執行階段組件來重新編譯。 相反地，用戶端程式會繼續使用執行階段組件適用的任何版本，並針對公用介面使用內嵌的類型資訊。  
  
 由於類型內嵌的主要功能是支援透過 COM Interop 組件進行類型資訊內嵌，因此當您將類型資訊內嵌在完全受管理的解決方案中時，也會套用下列限制：  
  
-   只會內嵌 COM Interop 專屬的屬性，而忽略其他屬性。  
  
-   如果某類型使用泛型參數，而該泛型參數的類型是內嵌的類型，您就不能跨組件界限使用此類型。 跨組件界限的範例包括從其他組件呼叫方法，或透過定義於其他組件上的類型來衍生類型。  
  
-   系統不會內嵌常數。  
  
-   <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> 類別不支援內嵌類型作為索引鍵。 您可以實作自己的字典類型，以支援索引鍵形式的內嵌類型。  
  
 在這個逐步解說中，您將進行下列工作：  
  
-   建立具有公用介面的強式名稱組件，且該介面包含可內嵌的類型資訊。  
  
-   建立強式名稱的執行階段組件，以實作上述公用介面。  
  
-   建立用戶端程式，以內嵌公用介面的類型資訊，並從執行階段組件建立類別的執行個體。  
  
-   修改並重新建置執行階段組件。  
  
-   執行用戶端程式，查看是否正在使用新版本的執行階段組件，而不必重新編譯用戶端程式。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-an-interface"></a>建立介面  
  
#### <a name="to-create-the-type-equivalence-interface-project"></a>若要建立類型等價介面專案  
  
1.  在 Visual Studio 的 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]。  
  
2.  在 [新增專案] 對話方塊的 [專案類型] 窗格中，確認已選取 [Windows]。 在 [範本] 窗格中，選取 [類別庫]。 在 [名稱] 方塊中，輸入 `TypeEquivalenceInterface` 並按一下 [確定]。 隨即會建立新專案。  
  
3.  在**方案總管 中**，Class1.vb 檔案上按一下滑鼠右鍵，然後按一下**重新命名**。 將檔案重新命名為 `ISampleInterface.vb`，然後按 ENTER。 重新命名檔案時，也會將類別重新命名為 `ISampleInterface`。 這個類別將代表類別的公用介面。  
  
4.  以滑鼠右鍵按一下 TypeEquivalenceInterface 專案，然後按一下 [屬性]。 按一下 [編譯] 索引標籤。將輸出路徑設為開發電腦上的有效位置，例如 `C:\TypeEquivalenceSample`。 這個位置也會用於本逐步解說稍後的步驟。  
  
5.  在編輯專案屬性期間，按一下 [簽署] 索引標籤。選取 [簽署組件] 選項。 在 [選擇強式名稱金鑰檔案] 清單中，按一下 [<新增...>]。 在 [金鑰檔案名稱] 方塊中，輸入 `key.snk`。 清除 [以密碼保護我的金鑰檔] 核取方塊。 按一下 [確定]。  
  
6.  開啟 ISampleInterface.vb 檔案。 將下列程式碼加入 ISampleInterface 類別檔案，以建立 ISampleInterface 介面。  
  
    ```vb  
    Imports System.Runtime.InteropServices  
  
    <ComImport()>  
    <Guid("8DA56996-A151-4136-B474-32784559F6DF")>  
    Public Interface ISampleInterface  
        Sub GetUserInput()  
        ReadOnly Property UserInput As String  
    End Interface  
    ```  
  
7.  在 [工具] 功能表上，按一下 [建立 GUID]。 在 [建立 GUID] 對話方塊中，依序按一下 [登錄格式] 和 [複製]。 按一下 [結束] 。  
  
8.  刪除 `Guid` 屬性中的範例 GUID，然後貼上您從 [建立 GUID] 對話方塊所複製的 GUID。 移除已複製 GUID 的大括號 ({})。  
  
9. 在 [專案] 功能表上，按一下 [顯示所有檔案]。  
  
10. 在**方案總管 中**，依序展開**我的專案**資料夾。 按兩下 AssemblyInfo.vb。 將下列屬性加入檔案中。  
  
    ```vb  
    <Assembly: ImportedFromTypeLib("")>  
    ```  
  
     儲存檔案。  
  
11. 儲存專案。  
  
12. 以滑鼠右鍵按一下 TypeEquivalenceInterface 專案，然後按一下 [建置]。 即會編譯類別庫 .dll 檔案，並將其儲存至指定的建置輸出路徑 (例如 C:\TypeEquivalenceSample)。  
  
## <a name="creating-a-runtime-class"></a>建立執行階段類別  
  
#### <a name="to-create-the-type-equivalence-runtime-project"></a>若要建立類型等價執行階段專案  
  
1.  在 Visual Studio 的 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]。  
  
2.  在 [新增專案] 對話方塊的 [專案類型] 窗格中，確認已選取 [Windows]。 在 [範本] 窗格中，選取 [類別庫]。 在 [名稱] 方塊中，輸入 `TypeEquivalenceRuntime` 並按一下 [確定]。 隨即會建立新專案。  
  
3.  在**方案總管 中**，Class1.vb 檔案上按一下滑鼠右鍵，然後按一下**重新命名**。 將檔案重新命名為 `SampleClass.vb`，然後按 ENTER。 重新命名檔案時，也會將類別重新命名為 `SampleClass`。 此類別會實作 `ISampleInterface` 介面。  
  
4.  以滑鼠右鍵按一下 TypeEquivalenceRuntime 專案，然後按一下 [屬性]。 按一下 [編譯] 索引標籤。將輸出路徑設為您在 TypeEquivalenceInterface 專案中使用的相同位置，例如 `C:\TypeEquivalenceSample`。  
  
5.  在編輯專案屬性期間，按一下 [簽署] 索引標籤。選取 [簽署組件] 選項。 在 [選擇強式名稱金鑰檔案] 清單中，按一下 [<新增...>]。 在 [金鑰檔案名稱] 方塊中，輸入 `key.snk`。 清除 [以密碼保護我的金鑰檔] 核取方塊。 按一下 [確定]。  
  
6.  以滑鼠右鍵按一下 TypeEquivalenceRuntime 專案，然後按一下 [加入參考]。 按一下 [瀏覽] 索引標籤，並瀏覽至輸出路徑資料夾。 選取 TypeEquivalenceInterface.dll 檔案，然後按一下 [確定]。  
  
7.  在 [專案] 功能表上，按一下 [顯示所有檔案]。  
  
8.  展開方案總管中的 [參考] 資料夾。 選取 TypeEquivalenceInterface 參考。 在 TypeEquivalenceInterface 參考的 [屬性] 視窗中，將 [特定版本] 屬性設為 [False]。  
  
9. 將下列程式碼加入 SampleClass 類別檔案中，以建立 SampleClass 類別。  
  
    ```vb  
    Imports TypeEquivalenceInterface  
  
    Public Class SampleClass  
        Implements ISampleInterface  
  
        Private p_UserInput As String  
        Public ReadOnly Property UserInput() As String Implements ISampleInterface.UserInput  
            Get  
                Return p_UserInput  
            End Get  
        End Property  
  
        Public Sub GetUserInput() Implements ISampleInterface.GetUserInput  
            Console.WriteLine("Please enter a value:")  
            p_UserInput = Console.ReadLine()  
        End Sub  
    End Class  
    ```  
  
10. 儲存專案。  
  
11. 以滑鼠右鍵按一下 TypeEquivalenceRuntime 專案，然後按一下 [建置]。 即會編譯類別庫 .dll 檔案，並將其儲存至指定的建置輸出路徑 (例如 C:\TypeEquivalenceSample)。  
  
## <a name="creating-a-client-project"></a>建立用戶端專案  
  
#### <a name="to-create-the-type-equivalence-client-project"></a>若要建立類型等價用戶端專案  
  
1.  在 Visual Studio 的 [檔案] 功能表上，指向 [新增]，然後按一下 [專案]。  
  
2.  在 [新增專案] 對話方塊的 [專案類型] 窗格中，確認已選取 [Windows]。 選取 [範本] 窗格中的 [主控台應用程式]。 在 [名稱] 方塊中，輸入 `TypeEquivalenceClient` 並按一下 [確定]。 隨即會建立新專案。  
  
3.  以滑鼠右鍵按一下 TypeEquivalenceClient 專案，然後按一下 [屬性]。 按一下 [編譯] 索引標籤。將輸出路徑設為您在 TypeEquivalenceInterface 專案中使用的相同位置，例如 `C:\TypeEquivalenceSample`。  
  
4.  以滑鼠右鍵按一下 TypeEquivalenceClient 專案，然後按一下 [加入參考]。 按一下 [瀏覽] 索引標籤，並瀏覽至輸出路徑資料夾。 選取 TypeEquivalenceInterface.dll 檔案 (而不是 TypeEquivalenceRuntime.dll)，然後按一下 [確定]。  
  
5.  在 [專案] 功能表上，按一下 [顯示所有檔案]。  
  
6.  展開方案總管中的 [參考] 資料夾。 選取 TypeEquivalenceInterface 參考。 在 TypeEquivalenceInterface 參考的 [屬性] 視窗中，將 [內嵌 Interop 類型] 屬性設為 [True]。  
  
7.  將下列程式碼加入至要建立用戶端程式的 Module1.vb 檔案。  
  
    ```vb  
    Imports TypeEquivalenceInterface  
    Imports System.Reflection  
  
    Module Module1  
  
        Sub Main()  
            Dim sampleAssembly = Assembly.Load("TypeEquivalenceRuntime")  
            Dim sampleClass As ISampleInterface = CType( _  
                sampleAssembly.CreateInstance("TypeEquivalenceRuntime.SampleClass"), ISampleInterface)  
            sampleClass.GetUserInput()  
            Console.WriteLine(sampleClass.UserInput)  
            Console.WriteLine(sampleAssembly.GetName().Version)  
            Console.ReadLine()  
        End Sub  
  
    End Module  
    ```  
  
8.  按 CTRL+F5 建置並執行程式。  
  
## <a name="modifying-the-interface"></a>修改介面  
  
#### <a name="to-modify-the-interface"></a>若要修改介面  
  
1.  在 Visual Studio 的 [檔案] 功能表上，指向 [開啟]，然後按一下 [專案/方案]。  
  
2.  在 [開啟] 對話方塊中，以滑鼠右鍵按一下 TypeEquivalenceInterface 專案，然後按一下 [屬性]。 按一下 [應用程式]  索引標籤。按一下 [組件資訊] 按鈕。 將 [組件版本] 和 [檔案版本] 的值變更為 `2.0.0.0`。  
  
3.  開啟 ISampleInterface.vb 檔案。 將下列程式碼行加入 ISampleInterface 介面。  
  
    ```vb  
    Function GetDate() As Date  
    ```  
  
     儲存檔案。  
  
4.  儲存專案。  
  
5.  以滑鼠右鍵按一下 TypeEquivalenceInterface 專案，然後按一下 [建置]。 即會編譯新版本的類別庫 .dll 檔案，並將其儲存在指定的建置輸出路徑中 (例如 C:\TypeEquivalenceSample)。  
  
## <a name="modifying-the-runtime-class"></a>修改執行階段類別  
  
#### <a name="to-modify-the-runtime-class"></a>若要修改執行階段類別  
  
1.  在 Visual Studio 的 [檔案] 功能表上，指向 [開啟]，然後按一下 [專案/方案]。  
  
2.  在 [開啟] 對話方塊中，以滑鼠右鍵按一下 TypeEquivalenceRuntime 專案，然後按一下 [屬性]。 按一下 [應用程式]  索引標籤。按一下 [組件資訊] 按鈕。 將 [組件版本] 和 [檔案版本] 的值變更為 `2.0.0.0`。  
  
3.  開啟 SampleClass.vbfile。 將下列幾行程式碼加入 SampleClass 類別。  
  
```vb  
Public Function GetDate() As DateTime Implements ISampleInterface.GetDate  
    Return Now  
End Function  
```  
  
     Save the file.  
  
4.  儲存專案。  
  
5.  以滑鼠右鍵按一下 TypeEquivalenceRuntime 專案，然後按一下 [建置]。 即會編譯更新版本的類別庫 .dll 檔案，並將其儲存在之前指定的建置輸出路徑中 (例如 C:\TypeEquivalenceSample)。  
  
6.  在檔案總管中，開啟輸出路徑資料夾 (例如 C:\TypeEquivalenceSample)。 按兩下 TypeEquivalenceClient.exe 以執行程式。 程式即會反映新版本的 TypeEquivalenceRuntime 組件，而不需重新編譯。  
  
## <a name="see-also"></a>另請參閱  
 [/link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md)  
 [程式設計概念](../../../../visual-basic/programming-guide/concepts/index.md)  
 [使用組件設計程式](../../../../framework/app-domains/programming-with-assemblies.md)  
 [組件和全域組件快取 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)
