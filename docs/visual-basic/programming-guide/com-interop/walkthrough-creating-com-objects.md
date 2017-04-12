---
title: "逐步解說︰ 使用 Visual Basic 建立 COM 物件 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- COM interop, creating COM objects
- COM objects, creating
- COM interop, walkthroughs
- object creation, COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
caps.latest.revision: 30
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: cce28e2be5914880107334bf2c4dc4dc645b4793
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a>逐步解說：使用 Visual Basic 建立 COM 物件
建立新的應用程式或元件時，最好建立.NET Framework 組件。 不過，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]也方便您公開給 COM 的.NET Framework 元件 這可讓您提供新的元件需要的 COM 元件的舊版應用程式套件。 本逐步解說示範如何使用[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]公開[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]物件當做 COM 物件，使用和不 COM 類別樣板。  
  
 公開 COM 物件的最簡單方式是使用 COM 類別樣板。 COM 類別範本建立新的類別，並設定您的專案產生的 COM 物件的類別以及交互操作層，並向作業系統註冊。  
  
> [!NOTE]
>  雖然您也可以公開類別中建立[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]為 unmanaged 程式碼使用 COM 物件，它不是真正的 COM 物件，並且無法由[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。 如需詳細資訊，請參閱[.NET Framework 應用程式中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a>若要使用 COM 類別樣板建立 COM 物件  
  
1.  開啟新的 Windows 應用程式專案，從**檔案**功能表按一下**新的專案**。  
  
2.  在**新的專案**對話方塊下的**專案類型**欄位中，檢查是否已選取 Windows。 選取**類別庫**從**範本**清單，然後再按**確定**。 會顯示新的專案。  
  
3.  選取**加入新項目**從**專案**功能表。 **加入新項目**對話方塊隨即出現。  
  
4.  選取**COM 類別**從**範本**清單，然後再按**新增**。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]加入新的類別，並設定新的專案，COM interop。  
  
5.  加入 COM 類別程式碼，例如屬性、 方法和事件。  
  
6.  選取**建置 ClassLibrary1**從**建置**功能表。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]建置組件，並向作業系統註冊的 COM 物件。  
  
## <a name="creating-com-objects-without-the-com-class-template"></a>建立 COM 物件，而不需要的 COM 類別範本  
 您也可以建立 COM 類別，以手動方式而不是使用 COM 類別範本。 當您從命令列使用或您想要進一步控制定義 COM 物件的方式，此程序會很有幫助。  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a>若要設定您的專案，產生 COM 物件  
  
1.  開啟新的 Windows 應用程式專案，從**檔案**功能表按一下**NewProject**。  
  
2.  在**新的專案**對話方塊下的**專案類型**欄位中，檢查是否已選取 Windows。 選取**類別庫**從**範本**清單，然後再按**確定**。 會顯示新的專案。  
  
3.  在**方案總管 中**，以滑鼠右鍵按一下您的專案，然後按一下**屬性**。 **專案設計工具**隨即出現。  
  
4.  按一下 [編譯]**** 索引標籤。  
  
5.  選取**註冊 COM Interop**核取方塊。  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a>若要設定您的類別中的程式碼來建立 COM 物件  
  
1.  在**方案總管 中**，連按兩下**Class1.vb**以顯示其程式碼。  
  
2.  將類別重新命名為 `ComClass1`。  
  
3.  新增下列常數來`ComClass1`。 它們會儲存 COM 物件所擁有的全域唯一識別碼 (GUID) 常數。  
  
     [!code-vb[VbVbalrInterop #&2;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_1.vb)]  
  
4.  在**工具**] 功能表上，按一下 [**建立 Guid**。 在**建立 GUID**對話方塊中，按一下 **登錄格式**然後按一下 **複製**。 按一下 [結束] ****。  
  
5.  空字串，來取代`ClassId`具有 GUID，移除前置和後端在大括號。 例如，如果 Guidgen 所提供的 GUID 是`"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"`然後程式碼應該會出現，如下所示。  
  
     [!code-vb[VbVbalrInterop #&3;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_2.vb)]  
  
6.  重複上述步驟的`InterfaceId`和`EventsId`常數，如下列範例所示。  
  
     [!code-vb[VbVbalrInterop #&4;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_3.vb)]  
  
    > [!NOTE]
    >  請確定 Guid 的新的且唯一的。否則，與其他 COM 元件的 COM 元件可能發生衝突。  
  
7.  新增`ComClass`屬性設定為`ComClass1`，指定的類別 ID、 介面 ID 以及事件識別碼的 Guid，如下列範例所示︰  
  
     [!code-vb[VbVbalrInterop #&5;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_4.vb)]  
  
8.  COM 類別必須具有無參數`Public Sub New()`建構函式或類別會不正確地登錄。 將無參數建構函式加入至類別︰  
  
     [!code-vb[VbVbalrInterop #&6;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_5.vb)]  
  
9. 將屬性、 方法和事件加入至類別，它與結束`End Class`陳述式。 選取**建置方案**從**建置**功能表。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]建置組件，並向作業系統註冊的 COM 物件。  
  
    > [!NOTE]
    >  產生具有 COM 物件[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]不可由其他[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]應用程式因為它們不是，則為 true 的 COM 物件。 嘗試將參考加入至這類 COM 物件將會引發錯誤。 如需詳細資訊，請參閱[.NET Framework 應用程式中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.ComClassAttribute></xref:Microsoft.VisualBasic.ComClassAttribute>   
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)   
 [逐步解說︰ 實作 COM 物件的繼承](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)   
 [#Region 指示詞](../../../visual-basic/language-reference/directives/region-directive.md)   
 [.NET Framework 應用程式中的 COM 互通性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)   
 [互通性的疑難排解](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
