---
title: 逐步解說：使用 Visual Basic 建立 COM 物件
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: 39012ebdd8946f707fe459cb09bb2bbfc8e50088
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958272"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a>逐步解說：使用 Visual Basic 建立 COM 物件
建立新的應用程式或元件時, 最好建立 .NET Framework 元件。 不過, Visual Basic 也可以輕鬆地將 .NET Framework 元件公開給 COM。 這可讓您針對需要 COM 元件的繼承應用程式套件, 提供新的元件。 本逐步解說示範如何使用 Visual Basic 將 .NET Framework 物件公開為 COM 物件, 而不論是否使用 COM 類別樣板。  
  
 公開 COM 物件的最簡單方式是使用 COM 類別範本。 COM 類別範本會建立新的類別, 然後將您的專案設定為產生類別和互通性層做為 COM 物件, 並向作業系統註冊它。  
  
> [!NOTE]
> 雖然您也可以將 Visual Basic 中建立的類別公開為 COM 物件, 以供非受控程式碼使用, 但它並不是真正的 COM 物件, 而且無法由 Visual Basic 使用。 如需詳細資訊, 請參閱[.NET Framework 應用程式中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a>若要使用 COM 類別範本來建立 COM 物件  
  
1. 按一下 [**新增專案**], 從 [檔案] 功能表開啟新的 Windows 應用程式專案。  
  
2. 在 [**新增專案**] 對話方塊的 [**專案類型**] 欄位底下, 檢查是否已選取 [Windows]。 從 [**範本**] 清單中選取 [**類別庫**], 然後按一下 **[確定]** 。 隨即顯示新專案。  
  
3. 從 [**專案**] 功能表中選取 [**加入新專案**]。 隨即顯示 [ 新增項目] 對話方塊。  
  
4. 從 [**範本**] 清單中選取 [ **COM 類別**], 然後按一下 [**新增**]。 Visual Basic 加入新的類別, 並為 COM Interop 設定新的專案。  
  
5. 將屬性、方法和事件等程式碼加入 COM 類別。  
  
6. 從 [**建立**] 功能表中選取 [**組建 ClassLibrary1** ]。 Visual Basic 會建立元件, 並向作業系統註冊 COM 物件。  
  
## <a name="creating-com-objects-without-the-com-class-template"></a>不搭配 COM 類別樣板來建立 COM 物件  
 您也可以手動建立 COM 類別, 而不使用 COM 類別範本。 當您從命令列工作時, 或當您想要更充分掌控 COM 物件的定義時, 此程式會很有説明。  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a>若要設定您的專案以產生 COM 物件  
  
1. 按一下 [檔案] 功能表中的 [ **NewProject**], 以開啟新的 Windows 應用程式專案。  
  
2. 在 [**新增專案**] 對話方塊的 [**專案類型**] 欄位底下, 檢查是否已選取 [Windows]。 從 [**範本**] 清單中選取 [**類別庫**], 然後按一下 **[確定]** 。 隨即顯示新專案。  
  
3. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後按一下 [屬性]。 隨即顯示 [**專案設計**工具]。  
  
4. 按一下 [編譯] 索引標籤。  
  
5. 選取 [**註冊 COM Interop** ] 核取方塊。  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a>若要在您的類別中設定程式碼來建立 COM 物件  
  
1. 在**方案總管**中, 按兩下 [ **Class1** ] 以顯示其程式碼。  
  
2. 將類別重新命名為 `ComClass1`。  
  
3. 將下列常數新增至`ComClass1`。 它們會儲存 COM 物件必須擁有的全域唯一識別碼 (GUID) 常數。  
  
     [!code-vb[VbVbalrInterop#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#2)]  
  
4. 在 [工具] 功能表上，按一下 [建立 GUID]。 在 [建立 GUID] 對話方塊中，依序按一下 [登錄格式] 和 [複製]。 按一下 [結束]。  
  
5. 將的`ClassId`空字串取代為 GUID, 移除開頭和尾端的大括弧。 例如, 如果 Guidgen 所提供的 GUID 是`"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` , 則您的程式碼應該會如下所示。  
  
     [!code-vb[VbVbalrInterop#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#3)]  
  
6. 針對`InterfaceId` 和`EventsId`常數重複上述步驟, 如下列範例所示。  
  
     [!code-vb[VbVbalrInterop#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#4)]  
  
    > [!NOTE]
    > 請確定 Guid 是新的, 而且是唯一的;否則, 您的 COM 元件可能會與其他 COM 元件衝突。  
  
7. 將屬性新增至`ComClass1`, 並指定類別識別碼、介面識別碼和事件識別碼的 guid, 如下列範例所示: `ComClass`  
  
     [!code-vb[VbVbalrInterop#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#5)]  
  
8. COM 類別必須有無參數`Public Sub New()`的函式, 否則類別將不會正確地註冊。 將無參數的構造函式新增至類別:  
  
     [!code-vb[VbVbalrInterop#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#6)]  
  
9. 將屬性、方法和事件加入至類別, 並以`End Class`語句結束。 從 [**建立**] 功能表中選取 [**建立方案**]。 Visual Basic 會建立元件, 並向作業系統註冊 COM 物件。  
  
    > [!NOTE]
    > 您使用 Visual Basic 產生的 COM 物件無法供其他 Visual Basic 應用程式使用, 因為它們不是真正的 COM 物件。 嘗試加入對這類 COM 物件的參考將會引發錯誤。 如需詳細資訊, 請參閱[.NET Framework 應用程式中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.ComClassAttribute>
- [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)
- [逐步解說：實作 COM 物件的繼承](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [#Region 指示詞](../../../visual-basic/language-reference/directives/region-directive.md)
- [.NET Framework 應用程式中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [互通性的疑難排解](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
