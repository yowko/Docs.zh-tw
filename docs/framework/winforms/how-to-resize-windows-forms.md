---
title: "如何：調整 Windows Form 的大小"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- resizing Windows Forms
- Windows Forms, resizing
ms.assetid: 5d9dd47e-e68c-48c9-a0a3-a9ff34ba009d
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc2e9f81094d16030dbe4595a8132569edab782a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resize-windows-forms"></a>如何：調整 Windows Form 的大小
您可以使用幾種方式來指定 Windows Form 的大小。 您可以為 <xref:System.Windows.Forms.Form.Size%2A> 屬性設定新值，或個別調整 <xref:System.Windows.Forms.Control.Height%2A> 或 <xref:System.Windows.Forms.Control.Width%2A> 屬性，以程式設計方式來變更表單的高度和寬度。 如果您使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]，可以利用 Windows Form 設計工具來變更大小。 另請參閱[How to： 使用設計工具調整 Windows Form](http://msdn.microsoft.com/library/37k2zkwx\(v=vs.110\))。  
  
### <a name="to-resize-a-form-programmatically"></a>以程式設計方式調整表單的大小  
  
-   設定表單的 <xref:System.Windows.Forms.Form.Size%2A> 屬性，在執行階段定義表單的大小。  
  
     下列程式碼範例示範將表單大小設定為 100 × 100 像素。  
  
    ```vb  
    Form1.Size = New System.Drawing.Size(100, 100)  
    ```  
  
    ```csharp  
    Form1.Size = new System.Drawing.Size(100, 100);  
    ```  
  
    ```cpp  
    Form1->Size = System::Drawing::Size(100, 100);  
    ```  
  
### <a name="to-change-form-width-and-height-programmatically"></a>以程式設計方式變更表單寬度和高度  
  
-   定義 <xref:System.Windows.Forms.Form.Size%2A> 之後，使用 <xref:System.Windows.Forms.Control.Width%2A> 或 <xref:System.Windows.Forms.Control.Height%2A> 屬性來變更表單高度或寬度。  
  
     下列程式碼範例示範將表單的寬度設定為 300 像素 (從表單的左邊緣算起)，而高度則維持不變。  
  
    ```vb  
    Form1.Width = 300  
    ```  
  
    ```csharp  
    Form1.Width = 300;  
    ```  
  
    ```cpp  
    Form1->Width = 300;  
    ```  
  
     -或-  
  
     設定 <xref:System.Windows.Forms.Form.Size%2A> 屬性來變更 <xref:System.Drawing.Size.Width%2A> 或 <xref:System.Drawing.Size.Height%2A>。  
  
     不過，如下列程式碼範例所示，這種方法比直接設定 <xref:System.Windows.Forms.Control.Width%2A> 或 <xref:System.Windows.Forms.Control.Height%2A> 屬性更困難。  
  
    ```vb  
    Form1.Size = New Size(300, Form1.Size.Height)  
    ```  
  
    ```csharp  
    Form1.Size = new Size(300, Form1.Size.Height);  
    ```  
  
    ```cpp  
    Form1->Size = System::Drawing::Size(300, Form1->Size.Height);  
    ```  
  
### <a name="to-change-form-size-by-increments-programmatically"></a>以程式設計方式遞增變更表單大小  
  
-   若要遞增表單的大小，請設定 <xref:System.Drawing.Size.Width%2A> 和 <xref:System.Drawing.Size.Height%2A> 屬性。  
  
     下列程式碼範例示範將表單的寬度設定為比目前設定還要寬 200 像素。  
  
    ```vb  
    Form1.Width += 200  
    ```  
  
    ```csharp  
    Form1.Width += 200;  
    ```  
  
    ```cpp  
    Form1->Width += 200;  
    ```  
  
    > [!CAUTION]
    >  除非您透過將 <xref:System.Windows.Forms.Form.Size%2A> 屬性設定為新的 <xref:System.Drawing.Size> 結構，來同時設定高度和寬度維度，否則請一律使用 <xref:System.Drawing.Size.Height%2A> 或 <xref:System.Drawing.Size.Width%2A> 屬性來變更表單的維度。 <xref:System.Windows.Forms.Form.Size%2A> 屬性會傳回實值類型的 <xref:System.Drawing.Size> 結構。 您無法指派新值給實值類型的屬性。 因此，下列程式碼範例將無法進行編譯。  
  
    ```vb  
    ' NOTE: CODE WILL NOT COMPILE  
    Dim f As New Form()  
    f.Size.Width += 100  
    ```  
  
    ```csharp  
    // NOTE: CODE WILL NOT COMPILE  
    Form f = new Form();  
    f.Size.Width += 100;  
    ```  
  
    ```cpp  
    // NOTE: CODE WILL NOT COMPILE  
    Form^ f = gcnew Form();  
    f->Size->X += 100;  
    ```  
  
## <a name="see-also"></a>請參閱  
 [Windows Forms 使用者入門](../../../docs/framework/winforms/getting-started-with-windows-forms.md)  
 [增強 Windows Forms 應用程式](../../../docs/framework/winforms/advanced/index.md)
