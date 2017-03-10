---
title: "My.Forms Object | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "My.Forms"
  - "My.MyProject.Forms"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Forms object"
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# My.Forms Object
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

提供可用於存取目前專案中所宣告之每個 Windows 表單執行個體的屬性。  
  
## 備註  
 `My.Forms` 物件提供目前專案中每個表單的執行個體。  屬性名稱和該屬性所存取的表單名稱相同。  如需將表單加入至專案的詳細資訊，請參閱 [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/zh-tw/3d7bb25f-fd90-47cf-9378-fa0d764686c1)。  
  
 您可以使用不含限定性條件的表單名稱存取 `My.Forms` 物件提供的表單。  由於屬性名稱和表單的型別名稱相同，因此可以存取表單，如同它已有預設執行個體。  例如，`My.Forms.Form1.Show` 等於 `Form1.Show`。  
  
 `My.Forms` 物件只會公開 \(Expose\) 與目前專案相關聯的表單。  它不會提供對所參考 DLL 內宣告之表單的存取。  若要存取 DLL 所提供的表單，您必須使用表單的限定名稱 \(Qualified Name\)，寫法為 *DllName*.*FormName*。  
  
 您可以使用 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> 屬性來取得應用程式中所有開啟表單的集合。  
  
 這個物件和它所有的屬性都只適用於 Windows 應用程式。  
  
## 屬性  
 `My.Forms` 物件的每個屬性都可以用於存取目前專案中的某個表單執行個體。  屬性名稱和該屬性所存取的表單名稱相同，而屬性型別 \(Property Type\) 則和表單的型別相同。  
  
> [!NOTE]
>  如果發生名稱衝突，存取表單的屬性名稱就是 *RootNamespace*\_*Namespace*\_*FormName*。  例如，假設有兩個名為 `Form1.` 的表單，如果其中一個表單位於根命名空間 `WindowsApplication1` 的命名空間 `Namespace1`，則必須透過 `My.Forms.WindowsApplication1_Namespace1_Form1` 存取該表單。  
  
 `My.Forms` 會提供應用程式啟動時所建立之主要表單的存取。  至於其他表單，`My.Forms` 物件會在存取表單時建立新的表單執行個體，並將它儲存起來。  以後只要存取該屬性，就會傳回該表單執行個體。  
  
 您可以將 `Nothing` 指派給表單的屬性，即可處置 \(Dispose\) 該表單。  屬性 Setter 會呼叫表單的 <xref:System.Windows.Forms.Form.Close%2A> 方法，然後將 `Nothing` 指派給儲存的值。  如果將 `Nothing` 以外的任何值指定給屬性，則 Setter 會擲回 <xref:System.ArgumentException> 例外狀況。  
  
 您可以使用 `Is` 或 `IsNot` 運算子，測試 `My.Forms` 物件的屬性是否儲存表單執行個體。  也可以使用這些運算子，檢查屬性的值是否為 `Nothing`。  
  
> [!NOTE]
>  通常，`Is` 或 `IsNot` 運算子必須讀取屬性值，才能執行比較作業。  但如果屬性目前是儲存 `Nothing`，則屬性會建立新的表單執行個體，然後傳回該執行個體。  不過，Visual Basic 編譯器會以不同的方式處理 `My.Forms` 物件的屬性，並允許 `Is` 或 `IsNot` 運算子檢查屬性的狀態，而不需改變屬性的值。  
  
## 範例  
 這個範例會變更預設 `SidebarMenu` 表單的標題。  
  
 [!code-vb[VbVbalrMyForms#2](../../../visual-basic/language-reference/objects/codesnippet/visualbasic/my-forms-object_1.vb)]  
  
 若要成功使用這個範例，您的專案必須具有名為 `SidebarMenu` 的表單。  如需詳細資訊，請參閱 [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/zh-tw/3d7bb25f-fd90-47cf-9378-fa0d764686c1)。  
  
 這個程式碼只適用於 Windows 應用程式專案。  
  
## 需求  
  
### 依專案類型的可用性  
  
|||  
|-|-|  
|專案類型|是否可用|  
|Windows 應用程式|**是**|  
|類別庫|否|  
|主控台應用程式|否|  
|Windows 控制項程式庫|否|  
|Web 控制項程式庫|否|  
|Windows 服務|否|  
|網站|否|  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>   
 <xref:System.Windows.Forms.Form>   
 <xref:System.Windows.Forms.Form.Close%2A>   
 [Objects](../../../visual-basic/language-reference/objects/index.md)   
 [How to: Add Windows Forms to a Project](http://msdn.microsoft.com/zh-tw/3d7bb25f-fd90-47cf-9378-fa0d764686c1)   
 [Is Operator](../../../visual-basic/language-reference/operators/is-operator.md)   
 [IsNot Operator](../../../visual-basic/language-reference/operators/isnot-operator.md)   
 [Accessing Application Forms](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)