---
title: "Walkthrough: Implementing Inheritance with COM Objects (Visual Basic) | Microsoft Docs"
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
  - "inheritance, COM reusability"
  - "base classes, COM reusability"
  - "inheritance, walkthroughs"
  - "derived classes, COM reusability"
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Walkthrough: Implementing Inheritance with COM Objects (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

您可以從 COM 物件中的 `Public` 類別衍生 Visual Basic 類別，即使這些物件是使用舊版 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 建立的也一樣。  從 COM 物件中所繼承類別的屬性和方法可以遭覆寫或多載，就如同其他基底類別的屬性和方法一樣。  當您有個現有類別庫 \(Class Library\) 而又不要加以重新編譯時，從 COM 物件繼承 \(Inheritance\) 就相當有用。  
  
 下列程序將說明如何使用 Visual Basic 6.0 建立包含類別的 COM 物件，然後將其當做基底類別使用。  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### 若要建立在本逐步解說中使用的 COM 物件  
  
1.  在 Visual Basic 6.0 中，開啟新的 ActiveX DLL 專案。  名為 `Project1` 的專案隨即建立，  其中包含名為 `Class1` 的類別。  
  
2.  在 \[**專案總管**\] 中，以滑鼠右鍵按一下 \[**Project1**\]，再按一下 \[**Project1 屬性**\]。  接著會顯示 \[**專案屬性**\] 對話方塊。  
  
3.  在 \[**專案屬性**\] 對話方塊的 \[**一般**\] 索引標籤中，在 \[**專案名稱**\] 欄位輸入 `ComObject1` 來變更專案名稱。  
  
4.  在 \[**專案總管**\] 中，以滑鼠右鍵按一下 `Class1`，再按一下 \[**屬性**\]。  接著會顯示類別的 \[**屬性**\] 視窗。  
  
5.  將 `Name` 屬性變更為 `MathFunctions`。  
  
6.  在 \[**專案總管**\] 中，以滑鼠右鍵按一下 `MathFunctions`，再按一下 \[**檢視程式碼**\]。  接著會顯示 \[**程式碼編輯器**\]。  
  
7.  加入區域變數來存放屬性值：  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8.  加入 Property `Let` 和 Property `Get` 屬性程序：  
  
    ```  
    Public Property Let Prop1(ByVal vData As Integer)  
       'Used when assigning a value to the property.  
       mvarProp1 = vData  
    End Property  
    Public Property Get Prop1() As Integer  
       'Used when retrieving a property's value.  
       Prop1 = mvarProp1  
    End Property  
    ```  
  
9. 加入一個函式：  
  
    ```  
    Function AddNumbers(   
       ByVal SomeNumber As Integer,   
       ByVal AnotherNumber As Integer) As Integer  
  
       AddNumbers = SomeNumber + AnotherNumber  
    End Function  
    ```  
  
10. 按一下 \[**檔案**\] 功能表上的 \[**製作 ComObject1.dll**\] 建立並註冊 COM 物件。  
  
    > [!NOTE]
    >  雖然您也可以將 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 建立的類別當做 COM 物件公開 \(Expose\)，但它不是真正的 COM 物件，所以不適用於本逐步解說內容。  如需詳細資訊，請參閱 [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)。  
  
## Interop 組件  
 在下列程序中，您會建立 Interop 組件來當做 Unmanaged 程式碼 \(例如 COM 物件\) 和 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] 使用的 Managed 程式碼之間的連結橋樑。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 建立的 Interop 組件會處理使用 COM 物件的許多細節，例如「*Interop 封送處理*」\(Interop Marshaling\)，此程序會在與 COM 物件之間往返資料時，將參數封裝 \(Package\) 起來並傳回對等資料型別的值。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 應用程式中的參考會指向 Interop 組件，而不是實質的 COM 物件。  
  
#### 若要搭配 Visual Basic 2005 \(含\) 以後版本來使用 COM 物件  
  
1.  開啟新的 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] Windows 應用程式專案。  
  
2.  在 \[**專案**\] 功能表上，按一下 \[**加入參考**\]。  
  
     接著會顯示 \[**加入參考**\] 對話方塊。  
  
3.  在 \[**COM**\] 索引標籤內，按兩下 \[**元件名稱**\] 清單中的 `ComObject1`，然後按一下 \[**確定**\]。  
  
4.  在 \[**專案**\] 功能表上，按一下 \[**加入新項目**\]。  
  
     接著會顯示 \[**加入新項目**\] 對話方塊。  
  
5.  在 \[**範本**\] 窗格中，按一下 \[**類別**\]。  
  
     在 \[**名稱**\] 欄位中出現預設檔名 `Class1.vb`。  將這個欄位變更為 MathClass.vb 並按一下 \[**加入**\]。  這會建立名為 `MathClass` 的類別並顯示它的程式碼。  
  
6.  將下列程式碼加到 `MathClass` 的上方以繼承自 COM 類別。  
  
     [!code-vb[VbVbalrInterop#31](../../../visual-basic/programming-guide/com-interop/codesnippet/visualbasic/vbvbalrinterop/Class1.vb#31)]  
  
7.  將下列程式碼加入至 `MathClass` 以多載基底類別的公用方法：  
  
     [!code-vb[VbVbalrInterop#32](../../../visual-basic/programming-guide/com-interop/codesnippet/visualbasic/vbvbalrinterop/Class1.vb#32)]  
  
8.  將下列程式碼加入至 `MathClass` 來擴充繼承類別：  
  
     [!code-vb[VbVbalrInterop#33](../../../visual-basic/programming-guide/com-interop/codesnippet/visualbasic/vbvbalrinterop/Class1.vb#33)]  
  
 新的類別會繼承 COM 物件中基底類別的屬性、多載方法並定義新的方法來擴充類別。  
  
#### 若要測試繼承的類別  
  
1.  在啟動表單中加入一個按鈕，然後按兩下按鈕來檢視其程式碼。  
  
2.  在按鈕的 `Click` 事件處理常式程序中加入下列程式碼，以建立 `MathClass` 的執行個體並呼叫多載方法：  
  
     [!code-vb[VbVbalrInterop#34](../../../visual-basic/programming-guide/com-interop/codesnippet/visualbasic/vbvbalrinterop/Class1.vb#34)]  
  
3.  按 F5 執行專案。  
  
 當您按一下表單上的按鈕時，首先會呼叫內含 `Short` 資料型別數字的 `AddNumbers` 方法，然後 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會從基底類別選擇適當的方法。  對 `AddNumbers` 的第二次呼叫會導向至 `MathClass` 的多載方法。  第三次呼叫會呼叫擴充類別的 `SubtractNumbers` 方法。  接著就會設定基底類別中的屬性並顯示值。  
  
## 後續步驟  
 您可能會注意到，多載 `AddNumbers` 函式的資料型別正好與繼承自 COM 物件中基底類別的方法相同。  這是因為基底類別方法的引數和參數在 Visual Basic 6.0 中是定義為 16 位元整數，但在 Visual Basic 的以後版本中則公開為 `Short` 型別的 16 位元整數。  新的函式接受 32 位元整數並且多載基底類別函式。  
  
 當使用 COM 物件時，請確實驗證參數的大小和資料型別。  例如，當使用接受 Visual Basic 6.0 集合物件 \(Collection Object\) 當做引數的 COM 物件時，您就不能提供 Visual Basic 以後版本的集合。  
  
 繼承自 COM 類別的屬性和方法可以被覆寫，這表示您可以宣告區域屬性或方法，以取代繼承自基底 COM 類別的屬性或方法。  覆寫繼承的 COM 屬性的規則和覆寫其他屬性和方法的規則相似，以下為不同處：  
  
-   如果您覆寫任何繼承自 COM 類別的屬性或方法，您必須覆寫所有其他繼承的屬性和方法。  
  
-   無法覆寫使用 `ByRef` 參數的屬性。  
  
## 請參閱  
 [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)   
 [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [Short Data Type](../../../visual-basic/language-reference/data-types/short-data-type.md)