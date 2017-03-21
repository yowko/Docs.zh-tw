---
title: "逐步解說︰ 從內嵌類型 Managed 組件，在 Visual Studio (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 56ed12ba-adff-4e9c-a668-7fcba80c4795
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: adc58e081cd9b874a841d84b11d92cbffb6ba6b8
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-visual-basic"></a>逐步解說︰ 在 Visual Studio (Visual Basic) 中內嵌 Managed 組件的類型
內嵌強式名稱的 managed 組件的類型資訊時，您可以鬆散結合達成版本獨立應用程式中的型別。 也就是您的程式可以寫入使用 managed 程式庫的多個版本的型別，而不需重新編譯每個版本。  
  
 使用 COM interop，例如從 Microsoft Office 使用 automation 物件的應用程式經常使用內嵌型別。 內嵌類型資訊，可讓相同組建的程式以使用不同版本的 Microsoft Office 的不同電腦上。 不過，您也可以使用內嵌的完全受管理的解決方案類型。  
  
 可以具有下列特性的組件內嵌類型資訊︰  
  
-   組件會公開一個以上的公用介面。  
  
-   內嵌的介面必須標註`ComImport`屬性和`Guid`屬性 （和唯一的 GUID）。  
  
-   組件以註解`ImportedFromTypeLib`屬性或`PrimaryInteropAssembly`屬性及組件層級`Guid`屬性。 (根據預設，Visual Basic 專案範本會包含組件層級`Guid`屬性。)  
  
 指定可內嵌的公用介面之後，您可以建立實作這些介面的執行階段類別。 用戶端程式由參考該組件包含的公用介面和設定，然後內嵌這些介面的型別資訊，在設計階段`Embed Interop Types`屬性參考的`True`。 這相當於使用命令列編譯器，並使用參考組件`/link`編譯器選項。 用戶端程式可以載入執行階段物件的型別為介面的執行個體。 如果您建立強式名稱的執行階段組件的新版本時，用戶端程式沒有更新的執行階段組件重新編譯。 相反地，用戶端程式會繼續使用執行階段組件的任何版本都提供，針對公用介面使用內嵌的類型資訊。  
  
 因為內嵌類型的主要功能是支援的 COM interop 組件的類型資訊內嵌，當您將類型資訊內嵌在完全受管理的解決方案，也會套用下列限制︰  
  
-   只有屬性特定 COM interop 會內嵌。其他屬性都會被忽略。  
  
-   如果型別會使用泛用參數的泛型參數的型別是內嵌的型別，該類型不能跨組件界限。 組件界限的範例包括從另一個組件呼叫方法，或從型別衍生型別定義於另一個組件。  
  
-   常數不會內嵌。  
  
-   <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>類別不支援內嵌的型別做為索引鍵。</xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName> 您可以實作自己的字典類型，以支援做為索引鍵為內嵌的類型。  
  
 在本逐步解說中，您將會執行下列作業︰  
  
-   建立強式名稱組件具有公用的介面，其中包含可內嵌類型資訊。  
  
-   建立強式名稱的執行階段組件實作的公用介面。  
  
-   建立用戶端程式內嵌的公用介面的型別資訊，從執行階段組件建立類別的執行個體。  
  
-   修改並重新建置執行階段組件。  
  
-   若要查看新版本的執行階段組件，而無須重新編譯用戶端程式正在使用用戶端程式執行。  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## <a name="creating-an-interface"></a>建立介面  
  
#### <a name="to-create-the-type-equivalence-interface-project"></a>若要建立類型等價介面專案  
  
1.  在 Visual Studio 中，在**檔案**功能表上，指向**新增**然後按一下 **專案**。  
  
2.  在**新的專案**對話方塊中，於**專案類型** 窗格中，請確定**Windows**已選取。 選取**類別庫**中**範本**窗格。 在**名稱**方塊中，輸入`TypeEquivalenceInterface`，然後按一下 **確定**。 建立新的專案。  
  
3.  在**方案總管 中**，Class1.vb 檔案上按一下滑鼠右鍵，然後按一下**重新命名**。 若要將檔案重新命名`ISampleInterface.vb`按下 ENTER。 重新命名檔案也會重新命名類別來`ISampleInterface`。 這個類別將代表類別的公用介面。  
  
4.  TypeEquivalenceInterface 專案上按一下滑鼠右鍵，然後按一下 **屬性**。 按一下 [編譯]**** 索引標籤。 輸出路徑設定有效的位置，在開發電腦，例如`C:\TypeEquivalenceSample`。 此位置也會用於在此逐步解說稍後的步驟。  
  
5.  仍在編輯專案屬性，然後按一下**簽署** 索引標籤。 選取**簽署組件**選項。 在**選擇強式名稱金鑰檔**清單中，按一下** <New...> **。</New...> 在**金鑰檔名稱**方塊中，輸入`key.snk`。 清除**保護我的密碼金鑰檔**核取方塊。 按一下 [確定]****。  
  
6.  開啟 ISampleInterface.vb 檔案。 若要建立 ISampleInterface 介面 ISampleInterface 類別檔案中加入下列程式碼。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
7.  在**工具**] 功能表上，按一下 [**建立 Guid**。 在**建立 GUID**對話方塊中，按一下 **登錄格式**然後按一下 **複製**。 按一下 [結束] ****。  
  
8.  在`Guid`屬性、 刪除範例 GUID，然後貼上您所複製的 GUID**建立 GUID**對話方塊。 移除大括號 （{}） 從已複製的 GUID。  
  
9. 在**專案**] 功能表上，按一下 [**顯示所有檔案**。  
  
10. 在**方案總管 中**，依序展開**我的專案**資料夾。 按兩下 AssemblyInfo.vb。 將下列屬性加入至檔案。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
     儲存檔案。  
  
11. 儲存專案。  
  
12. TypeEquivalenceInterface 專案上按一下滑鼠右鍵，然後按一下 **建置**。 編譯並儲存至指定的組建輸出路徑 (例如，C:\TypeEquivalenceSample) 類別庫.dll 檔案。  
  
## <a name="creating-a-runtime-class"></a>建立執行階段類別  
  
#### <a name="to-create-the-type-equivalence-runtime-project"></a>若要建立類型等價執行階段專案  
  
1.  在 Visual Studio 中，在**檔案**功能表上，指向**新增**然後按一下 **專案**。  
  
2.  在**新的專案**對話方塊中，於**專案類型** 窗格中，請確定**Windows**已選取。 選取**類別庫**中**範本**窗格。 在**名稱**方塊中，輸入`TypeEquivalenceRuntime`，然後按一下 **確定**。 建立新的專案。  
  
3.  在**方案總管 中**，Class1.vb 檔案上按一下滑鼠右鍵，然後按一下**重新命名**。 若要將檔案重新命名`SampleClass.vb`按下 ENTER。 重新命名檔案也會重新命名類別來`SampleClass`。 這個類別會實作`ISampleInterface`介面。  
  
4.  TypeEquivalenceRuntime 專案上按一下滑鼠右鍵，然後按一下 **屬性**。 按一下 [編譯]**** 索引標籤。 輸出路徑設定為相同的位置，例如，在 TypeEquivalenceInterface 專案中，使用`C:\TypeEquivalenceSample`。  
  
5.  仍在編輯專案屬性，然後按一下**簽署** 索引標籤。 選取**簽署組件**選項。 在**選擇強式名稱金鑰檔**清單中，按一下** <New...> **。</New...> 在**金鑰檔名稱**方塊中，輸入`key.snk`。 清除**保護我的密碼金鑰檔**核取方塊。 按一下 [確定]****。  
  
6.  TypeEquivalenceRuntime 專案上按一下滑鼠右鍵，然後按一下 **加入參考**。 按一下 **瀏覽** 索引標籤上，瀏覽至 輸出路徑資料夾。 選取 TypeEquivalenceInterface.dll 檔案，然後按一下**確定**。  
  
7.  在**專案**] 功能表上，按一下 [**顯示所有檔案**。  
  
8.  在**方案總管 中**，依序展開**參考**資料夾。 選取 TypeEquivalenceInterface 參考。 TypeEquivalenceInterface 參考的 [屬性] 視窗中設定**特定版本**屬性**False**。  
  
9. 若要建立 SampleClass 類別 SampleClass 類別檔案中加入下列程式碼。  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
10. 儲存專案。  
  
11. TypeEquivalenceRuntime 專案上按一下滑鼠右鍵，然後按一下 **建置**。 編譯並儲存至指定的組建輸出路徑 (例如，C:\TypeEquivalenceSample) 類別庫.dll 檔案。  
  
## <a name="creating-a-client-project"></a>建立用戶端專案  
  
#### <a name="to-create-the-type-equivalence-client-project"></a>若要建立類型等價的用戶端專案  
  
1.  在 Visual Studio 中，在**檔案**功能表上，指向**新增**然後按一下 **專案**。  
  
2.  在**新的專案**對話方塊中，於**專案類型** 窗格中，請確定**Windows**已選取。 選取**主控台應用程式**中**範本**窗格。 在**名稱**方塊中，輸入`TypeEquivalenceClient`，然後按一下 **確定**。 建立新的專案。  
  
3.  TypeEquivalenceClient 專案上按一下滑鼠右鍵，然後按一下 **屬性**。 按一下 [編譯]**** 索引標籤。 輸出路徑設定為相同的位置，例如，在 TypeEquivalenceInterface 專案中，使用`C:\TypeEquivalenceSample`。  
  
4.  TypeEquivalenceClient 專案上按一下滑鼠右鍵，然後按一下 **加入參考**。 按一下 **瀏覽** 索引標籤上，瀏覽至 輸出路徑資料夾。 選取 TypeEquivalenceInterface.dll 檔案 (不 TypeEquivalenceRuntime.dll)，然後按一下**確定**。  
  
5.  在**專案**] 功能表上，按一下 [**顯示所有檔案**。  
  
6.  在**方案總管 中**，依序展開**參考**資料夾。 選取 TypeEquivalenceInterface 參考。 TypeEquivalenceInterface 參考的 [屬性] 視窗中設定**內嵌 Interop 類型**屬性**True**。  
  
7.  若要建立用戶端程式 Module1.vb 檔案中加入下列程式碼。  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
8.  按 CTRL + F5 以建置並執行程式。  
  
## <a name="modifying-the-interface"></a>修改介面  
  
#### <a name="to-modify-the-interface"></a>若要修改的介面  
  
1.  在 Visual Studio 中，在**檔案**功能表上，指向**開啟**，然後按一下 **專案/方案**。  
  
2.  在**開啟專案**對話方塊中，TypeEquivalenceInterface 專案上按一下滑鼠右鍵，然後按一下 **屬性**。 按一下 [應用程式] **** 索引標籤。 按一下 [**組件資訊**] 按鈕。 變更**組件版本**和**檔案版本**值`2.0.0.0`。  
  
3.  開啟 ISampleInterface.vb 檔案。 將下列程式碼行加入至 ISampleInterface 介面。  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
     儲存檔案。  
  
4.  儲存專案。  
  
5.  TypeEquivalenceInterface 專案上按一下滑鼠右鍵，然後按一下 **建置**。 編譯並儲存在指定的組建輸出路徑 (例如，C:\TypeEquivalenceSample) 中的類別庫.dll 檔案的新版本。  
  
## <a name="modifying-the-runtime-class"></a>修改執行階段類別  
  
#### <a name="to-modify-the-runtime-class"></a>若要修改執行階段類別  
  
1.  在 Visual Studio 中，在**檔案**功能表上，指向**開啟**，然後按一下 **專案/方案**。  
  
2.  在**開啟專案** 對話方塊，以滑鼠右鍵按一下 TypeEquivalenceRuntime 專案，然後按一下**屬性**。 按一下 [應用程式] **** 索引標籤。 按一下 [**組件資訊**] 按鈕。 變更**組件版本**和**檔案版本**值`2.0.0.0`。  
  
3.  開啟 SampleClass.vbfile。 將下列程式碼行加入至 SampleClass 類別。  
  
```vb  
Public Function GetDate() As DateTime Implements ISampleInterface.GetDate  
    Return Now  
End Function  
```  
  
     Save the file.  
  
4.  儲存專案。  
  
5.  TypeEquivalenceRuntime 專案上按一下滑鼠右鍵，然後按一下 **建置**。 編譯並儲存在先前指定的建置輸出路徑 (例如，C:\TypeEquivalenceSample) 類別庫.dll 檔案的更新的版本。  
  
6.  在 檔案總管 中，開啟 輸出路徑資料夾 (例如，C:\TypeEquivalenceSample)。 按兩下 TypeEquivalenceClient.exe 執行程式。 程式將會反映 TypeEquivalenceRuntime 組件的新版本，而不需重新編譯。  
  
## <a name="see-also"></a>另請參閱  
 [/link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md)   
 [程式設計概念](../../../../visual-basic/programming-guide/concepts/index.md)   
 [使用組件設計程式](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6)   
 [組件和全域組件快取 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)

