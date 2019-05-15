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
ms.openlocfilehash: 465f1d8141f51de179dbb4e963a8fcac8c09fa33
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592701"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a>逐步解說：使用 Visual Basic 建立 COM 物件
建立新的應用程式或元件時，最好是建立.NET Framework 組件。 不過，Visual Basic 也容易公開給 COM 的.NET Framework 元件 這可讓您針對需要 COM 元件的舊版應用程式套件中提供新元件。 本逐步解說示範如何使用 Visual Basic 來公開成 COM 物件，使用和不使用 COM 類別範本的.NET Framework 物件。  
  
 COM 物件公開 （expose） 的最簡單方式是使用 COM 類別範本。 使用 COM 類別範本會建立新的類別，並設定專案以產生類別和互通性層級為 COM 物件，並向作業系統註冊。  
  
> [!NOTE]
>  雖然您也可以公開為 COM 物件使用的 unmanaged 程式碼建立 Visual Basic 中的類別，它不是真正的 COM 物件，並無法供 Visual Basic。 如需詳細資訊，請參閱 < [.NET Framework 應用程式中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a>若要使用 COM 類別範本建立 COM 物件  
  
1. 開啟新的 Windows 應用程式專案，從**檔案**功能表中的按一下**新的專案**。  
  
2. 在 **新的專案**下方的對話方塊中**專案類型**欄位中，確認已選取 Windows。 選取 **類別庫**從**範本**清單，然後再按**確定**。 新的專案會顯示。  
  
3. 選取 **加入新項目**從**專案**功能表。 隨即顯示 [ 新增項目] 對話方塊。  
  
4. 選取  **COM 類別**從**範本**清單，然後再按**新增**。 Visual Basic 會加入新的類別，並設定新的專案，COM interop。  
  
5. 加入 COM 類別中的程式碼，例如屬性、 方法和事件。  
  
6. 選取 **建置 ClassLibrary1**從**建置**功能表。 Visual Basic 建置的組件，並向作業系統註冊的 COM 物件。  
  
## <a name="creating-com-objects-without-the-com-class-template"></a>建立 COM 物件，不使用 COM 類別範本  
 您也可以建立以手動方式而不是使用 COM 類別範本的 COM 類別。 當您正在從命令列或您想要更充分掌控如何定義 COM 物件，此程序是很有幫助。  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a>若要設定您的專案，以產生 COM 物件  
  
1. 開啟新的 Windows 應用程式專案，從**檔案**功能表中的按一下**NewProject**。  
  
2. 在 **新的專案**下方的對話方塊中**專案類型**欄位中，確認已選取 Windows。 選取 **類別庫**從**範本**清單，然後再按**確定**。 新的專案會顯示。  
  
3. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後按一下 [屬性]。 **專案設計工具**隨即出現。  
  
4. 按一下 [編譯] 索引標籤。  
  
5. 選取 **註冊 COM Interop**核取方塊。  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a>若要設定您的類別中的程式碼，來建立 COM 物件  
  
1. 在 **方案總管**，按兩下**Class1.vb**以顯示其程式碼。  
  
2. 將類別重新命名為 `ComClass1`。  
  
3. 下列將常數新增到`ComClass1`。 它們會儲存 COM 物件時需要有全域唯一識別碼 (GUID) 常數。  
  
     [!code-vb[VbVbalrInterop#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#2)]  
  
4. 在 [工具] 功能表上，按一下 [建立 GUID]。 在 [建立 GUID] 對話方塊中，依序按一下 [登錄格式] 和 [複製]。 按一下 [結束] 。  
  
5. 取代為空字串`ClassId`guid，移除前置和尾端括號。 例如，如果 Guidgen 所提供的 GUID 是`"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"`則您的程式碼應該會出現，如下所示。  
  
     [!code-vb[VbVbalrInterop#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#3)]  
  
6. 重複上一個步驟`InterfaceId`和`EventsId`常數，如下列範例所示。  
  
     [!code-vb[VbVbalrInterop#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#4)]  
  
    > [!NOTE]
    >  請確定 Guid 的新的且唯一的;否則，您的 COM 元件可能發生衝突，與其他 COM 元件。  
  
7. 新增`ComClass`屬性設定為`ComClass1`，指定類別識別碼、 介面 ID 和事件識別碼的 Guid，如下列範例所示：  
  
     [!code-vb[VbVbalrInterop#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#5)]  
  
8. COM 類別必須具有無參數`Public Sub New()`建構函式或類別不會註冊正確。 加入類別中的無參數建構函式：  
  
     [!code-vb[VbVbalrInterop#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#6)]  
  
9. 將屬性、 方法和事件新增至類別，並結束它與`End Class`陳述式。 選取 **建置方案**從**建置**功能表。 Visual Basic 建置的組件，並向作業系統註冊的 COM 物件。  
  
    > [!NOTE]
    >  其他 Visual Basic 應用程式無法使用您產生與 Visual Basic 的 COM 物件，因為它們不是，則為 true 的 COM 物件。 嘗試將參考加入至這類 COM 物件會引發錯誤。 如需詳細資訊，請參閱 < [.NET Framework 應用程式中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.ComClassAttribute>
- [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)
- [逐步解說：實作 COM 物件的繼承](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [#Region 指示詞](../../../visual-basic/language-reference/directives/region-directive.md)
- [.NET Framework 應用程式中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [互通性的疑難排解](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
