---
title: "Walkthrough: Creating COM Objects with Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "COM interop, creating COM objects"
  - "COM objects, creating"
  - "COM interop, walkthroughs"
  - "object creation, COM objects"
  - "COM objects, walkthroughs"
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
caps.latest.revision: 30
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 30
---
# Walkthrough: Creating COM Objects with Visual Basic
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

建立新應用程式或元件時，最好建立 .NET Framework 組件。  然而，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 也能讓 .NET Framework 元件公開 \(Expose\) 至 COM 的工作變得更容易。  這可以讓您提供新元件給需要 COM 元件的舊版應用程式套件。  本逐步解說將示範在使用和未使用 COM 類別樣板 \(Template\) 的情況下，如何使用 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 將 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 物件公開為 COM 物件。  
  
 公開 COM 物件最簡單的方式是使用 COM 類別樣板。  COM 類別樣板會建立新類別，然後設定您的專案讓所產生的類別和互通 \(Interoperability\) 層成為 COM 物件，接著在作業系統上加以註冊。  
  
> [!NOTE]
>  雖然也可將使用 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 建立的類別公開為 COM 物件，以供 Unmanaged 程式碼使用，但它不是真正的 COM 物件，[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 無法使用它。  如需詳細資訊，請參閱 [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### 若要使用 COM 類別樣板來建立 COM 物件  
  
1.  按一下 \[**檔案**\] 功能表中的 \[**新增專案**\]，即可開啟新的 Windows 應用程式專案。  
  
2.  在 \[**新增專案**\] 對話方塊的 \[**專案類型**\] 欄位下，檢查是否已選取 Windows。  從 \[**樣板**\] 清單選取 \[**類別庫**\]，接著按一下 \[**確定**\]。  接著會出現新專案。  
  
3.  從 \[**專案**\] 功能表選取 \[**加入新項目**\]。  接著會顯示 \[**加入新項目**\] 對話方塊。  
  
4.  從 \[**樣板**\] 清單選取 \[**COM 類別**\]，然後按一下 \[**加入**\]。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 便會加入新的類別，並設定 COM Interop 的新專案。  
  
5.  將程式碼 \(例如屬性 \(Property\)、方法和事件\) 加入至 COM 類別。  
  
6.  從 \[**建置**\] 功能表選取 \[**建置 ClassLibrary1**\]。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 便會建置組件，並向作業系統註冊 COM 物件。  
  
## 不使用 COM 類別樣板建立 COM 物件  
 您也可以手動建立 COM 類別，而不需使用 COM 類別樣板。  在命令列執行作業或是要進一步控制定義 COM 物件的方式時，這個程序相當有用。  
  
#### 若要設定您的專案來產生 COM 物件  
  
1.  在 \[**檔案**\] 功能表中按一下 \[**新增專案**\]，開啟新的 Windows 應用程式專案。  
  
2.  在 \[**新增專案**\] 對話方塊的 \[**專案類型**\] 欄位下，檢查是否已選取 Windows。  從 \[**樣板**\] 清單選取 \[**類別庫**\]，接著按一下 \[**確定**\]。  接著會出現新專案。  
  
3.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下專案，然後按一下 \[**屬性**\]。  \[**專案設計工具**\] 隨即出現。  
  
4.  按一下 \[**編譯**\] 索引標籤。  
  
5.  選取 \[**註冊 COM Interop**\] 核取方塊。  
  
#### 若要在您的類別中設定程式碼來建立 COM 物件  
  
1.  在 \[**方案總管**\] 中，按兩下 \[**Class1.vb**\] 顯示其程式碼。  
  
2.  將類別重新命名為 `ComClass1`。  
  
3.  將下列常數加入至 `ComClass1`。  它們會儲存 COM 物件一定要有的全域唯一識別項 \(GUID\) 常數。  
  
     [!code-vb[VbVbalrInterop#2](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_1.vb)]  
  
4.  在 \[**工具**\] 功能表上按一下 \[**建立 GUID**\]。  在 \[**建立 GUID**\] 對話方塊中，按一下 \[**登錄格式**\]，再按一下 \[**複製**\]。  按一下 \[**結束**\]。  
  
5.  使用 GUID 取代 `ClassId` 的空白字串，且移除前後的大括號。  例如，如果 Guidgen 提供的 GUID 為 `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"`，則程式碼應看起來如下。  
  
     [!code-vb[VbVbalrInterop#3](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_2.vb)]  
  
6.  針對 `InterfaceId` 和 `EventsId` 常數，重複執行上述步驟 \(如下列範例所示\)。  
  
     [!code-vb[VbVbalrInterop#4](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_3.vb)]  
  
    > [!NOTE]
    >  確定 GUID 是新的且是唯一的，否則，COM 元件可能會與其他 COM 元件發生衝突。  
  
7.  將 `ComClass` 屬性 \(Attribute\) 加入至 `ComClass1`，為類別 ID、介面 ID 和事件 ID 指定 GUID，如下列範例所示：  
  
     [!code-vb[VbVbalrInterop#5](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_4.vb)]  
  
8.  COM 類別必須有無參數的 `Public Sub New()` 建構函式 \(Constructor\)，否則類別將無法正確註冊。  將無參數的建構函式加入至類別：  
  
     [!code-vb[VbVbalrInterop#6](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-creating-com-objects_5.vb)]  
  
9. 將屬性、方法和事件加入至類別，並以 `End Class` 陳述式結尾。  從 \[**建置**\] 功能表中選取 \[**建置方案**\]。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 便會建置組件，並向作業系統註冊 COM 物件。  
  
    > [!NOTE]
    >  其他 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 應用程式不可使用藉由 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 所產生的 COM 物件，原因是它們不是真正的 COM 物件。  嘗試將參考加入至這類 COM 物件將會引發錯誤。  如需詳細資訊，請參閱 [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.ComClassAttribute>   
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)   
 [Walkthrough: Implementing Inheritance with COM Objects](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)   
 [\#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md)   
 [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)   
 [Troubleshooting Interoperability](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)