---
title: 逐步解說：建立 COM 物件
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: 90a21b70b45902a9f4fd559a97e777f26043fffb
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075612"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a>逐步解說：使用 Visual Basic 建立 COM 物件

建立新的應用程式或元件時，最好是建立 .NET Framework 元件。 不過，Visual Basic 也可讓您輕鬆地將 .NET Framework 元件公開至 COM。 這可讓您為需要 COM 元件的繼承應用程式套件提供新元件。 本逐步解說示範如何使用 Visual Basic 將 .NET Framework 物件公開為 COM 物件，不論是否有 COM 類別範本。  
  
 公開 COM 物件最簡單的方式是使用 COM 類別範本。 此範本會建立新的類別，然後設定您的專案以使用交互操作層作為 COM 物件來產生類別，並將它註冊到作業系統。  
  
> [!NOTE]
> 雖然您也可以將 Visual Basic 中建立的類別公開為非受控程式碼要使用的 COM 物件，但它並不是真正的 COM 物件，Visual Basic 無法使用。 如需詳細資訊，請參閱 [.NET Framework 應用程式中的 COM 互通性](com-interoperability-in-net-framework-applications.md)。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a>使用 COM 類別範本來建立 COM 物件  
  
1. 按一下 [**新增專案**]，開啟 [檔案] 功能表**中的新**Windows 應用程式專案。  
  
2. 在 [ **新增專案** ] 對話方塊的 [ **專案類型** ] 欄位底下，檢查是否已選取 [Windows]。 從 [**範本**] 清單中選取 [**類別庫**]，然後按一下 **[確定]**。 新的專案隨即顯示。  
  
3. 從 [**專案**] 功能表中選取 [**加入新專案**]。 [ **加入新項目** ] 對話方塊隨即出現。  
  
4. 從 [**範本**] 清單中選取 [ **COM 類別**]，然後按一下 [**新增**]。 Visual Basic 加入新的類別，並設定 COM interop 的新專案。  
  
5. 將屬性、方法和事件等程式碼新增至 COM 類別。  
  
6. 從 [**組建**] 功能表選取 [**組建 ClassLibrary1** ]。 Visual Basic 會建立元件，並向作業系統註冊 COM 物件。  
  
## <a name="creating-com-objects-without-the-com-class-template"></a>建立不具 COM 類別範本的 COM 物件  

 您也可以手動建立 COM 類別，而不是使用 COM 類別範本。 當您從命令列執行時，或當您想要更充分掌控 COM 物件的定義時，此程式會很有説明。  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a>設定您的專案以產生 COM 物件  
  
1. 按一下 [檔案] 功能表 **中的 [** **NewProject**]，以開啟新的 Windows 應用程式專案。  
  
2. 在 [ **新增專案** ] 對話方塊的 [ **專案類型** ] 欄位底下，檢查是否已選取 [Windows]。 從 [**範本**] 清單中選取 [**類別庫**]，然後按一下 **[確定]**。 新的專案隨即顯示。  
  
3. 在 [方案總管]**** 中，以滑鼠右鍵按一下專案，然後按一下 [屬性]****。 [ **專案設計** 工具] 隨即顯示。  
  
4. 按一下 [編譯]**** 索引標籤。  
  
5. 選取 [ **註冊 COM Interop** ] 核取方塊。  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a>若要在您的類別中設定程式碼來建立 COM 物件  
  
1. 在 **方案總管**中，按兩下 [ **Class1** ] 以顯示其程式碼。  
  
2. 將類別重新命名為 `ComClass1`。  
  
3. 將下列常數加入至 `ComClass1` 。 它們會將全域唯一識別碼儲存 (GUID) 必須具有 COM 物件的常數。  
  
     [!code-vb[VbVbalrInterop#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#2)]  
  
4. 在 [工具]**** 功能表上，按一下 [建立 GUID]****。 在 [建立 GUID]**** 對話方塊中，依序按一下 [登錄格式]**** 和 [複製]****。 按一下 **[結束]**。  
  
5. 以 GUID 取代的空字串 `ClassId` ，移除開頭和尾端的大括弧。 例如，如果 Guidgen 所提供的 GUID， `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` 則您的程式碼應該會顯示如下。  
  
     [!code-vb[VbVbalrInterop#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#3)]  
  
6. 針對和常數重複上述步驟 `InterfaceId` `EventsId` ，如下列範例所示。  
  
     [!code-vb[VbVbalrInterop#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#4)]  
  
    > [!NOTE]
    > 請確定 Guid 是新的且唯一的。否則，您的 COM 元件可能會與其他 COM 元件發生衝突。  
  
7. 將 `ComClass` 屬性新增至 `ComClass1` ，並指定類別識別碼、介面識別碼和事件識別碼的 guid，如下列範例所示：  
  
     [!code-vb[VbVbalrInterop#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#5)]  
  
8. COM 類別必須有無參數的函式 `Public Sub New()` ，否則類別將無法正確註冊。 將無參數的函式新增至類別：  
  
     [!code-vb[VbVbalrInterop#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#6)]  
  
9. 將屬性、方法和事件加入至類別，並以 `End Class` 語句結尾。 從 [**組建**] 功能表選取 [**建立方案**]。 Visual Basic 會建立元件，並向作業系統註冊 COM 物件。  
  
    > [!NOTE]
    > 您使用 Visual Basic 產生的 COM 物件無法供其他 Visual Basic 應用程式使用，因為它們不是真正的 COM 物件。 嘗試加入這類 COM 物件的參考將會引發錯誤。 如需詳細資訊，請參閱 [.NET Framework 應用程式中的 COM 互通性](com-interoperability-in-net-framework-applications.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.ComClassAttribute>
- [COM Interop](index.md)
- [逐步解說：實作 COM 物件的繼承](walkthrough-implementing-inheritance-with-com-objects.md)
- [#Region 指示詞](../../language-reference/directives/region-directive.md)
- [.NET Framework 應用程式中的 COM 互通性](com-interoperability-in-net-framework-applications.md)
- [疑難排解互通性的問題](troubleshooting-interoperability.md)
