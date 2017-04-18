---
title: "如何：開發簡單的 Windows Form 控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Control 類別, Windows Form"
  - "控制項 [Windows Form]"
  - "自訂控制項 [Windows Form], 使用程式碼建立簡單控制項"
ms.assetid: 86cbe435-45b7-4cb4-9b5a-47418369758d
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 如何：開發簡單的 Windows Form 控制項
本章節逐步為您解說撰寫自訂 Windows Form 控制項的重要步驟。  這個逐步解說開發的簡單控制項允許您變更其 <xref:System.Windows.Forms.Control.Text%2A> 屬性的對齊。  它不會引發或處理事件。  
  
### 若要建立簡單自訂控制項  
  
1.  定義從 <xref:System.Windows.Forms.Control?displayProperty=fullName> 衍生的類別。  
  
    ```vb  
    Public Class FirstControl  
       Inherits Control  
  
    End Class  
    ```  
  
    ```csharp  
    public class FirstControl:Control{}  
    ```  
  
2.  定義屬性   \(您不需要定義屬性，因為控制項會從 <xref:System.Windows.Forms.Control> 類別繼承許多屬性，但大部分的自訂控制項通常會確實定義其他屬性\)。 下列程式碼片段定義名為 `TextAlignment`  的屬性，是 `FirstControl`  用來格式化繼承自 <xref:System.Windows.Forms.Control> 的 <xref:System.Windows.Forms.Control.Text%2A> 屬性的顯示。  如需定義屬性的詳細資訊，請參閱[屬性概觀](../Topic/Properties%20Overview.md)。  
  
     [!code-csharp[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]  
  
     當您設定會變更控制項視覺顯示的屬性時，您必須叫用 <xref:System.Windows.Forms.Control.Invalidate%2A> 方法來重繪控制項。  <xref:System.Windows.Forms.Control.Invalidate%2A> 是在基底類別 <xref:System.Windows.Forms.Control> 中定義的。  
  
3.  覆寫保護的 \(Protected\) <xref:System.Windows.Forms.Control.OnPaint%2A> 方法 \(繼承自 <xref:System.Windows.Forms.Control>\)，為控制項提供呈現邏輯。  如果您不覆寫 <xref:System.Windows.Forms.Control.OnPaint%2A>，您的控制項將無法自行繪圖。  在下列程式碼片段中，<xref:System.Windows.Forms.Control.OnPaint%2A> 方法以 `alignmentValue` 欄位所指定的對齊顯示繼承自 <xref:System.Windows.Forms.Control> 的 <xref:System.Windows.Forms.Control.Text%2A> 屬性。  
  
     [!code-csharp[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]  
  
4.  提供屬性給您的控制項。  屬性讓視覺設計工具能夠在設計階段適當顯示您的控制項和它的屬性和事件。  下列程式碼片段套用屬性於 `TextAlignment` 屬性。  在設計工具 \(例如 Visual Studio\) 中，<xref:System.ComponentModel.CategoryAttribute.Category%2A> 屬性 \(Attribute\)\(顯示於程式碼片段\) 會造成屬性 \(Property\) 顯示在邏輯分類之下。  <xref:System.ComponentModel.DescriptionAttribute.Description%2A> 屬性 \(Attribute\) 在 `TextAlignment` 屬性 \(Property\) 選取時，會導致說明字串顯示於 \[**屬性**\] 視窗底部。  如需屬性 \(Attribute\) 的詳細資訊，請參閱[元件的設計階段屬性](../Topic/Design-Time%20Attributes%20for%20Components.md)。  
  
     [!code-csharp[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]  
  
5.  \(選擇性\) 提供資源給您的控制項。  您可以使用編譯器選項 \(在 C\# 中為 `/res`\)，將資源與控制項一起封裝 \(Package\)，以提供資源 \(例如點陣圖\) 給控制項。  在執行階段時，可以使用 <xref:System.Resources.ResourceManager> 類別的方法來擷取資源。  如需建立和使用資源的詳細資訊，請參閱[桌面應用程式中的資源](../../../../docs/framework/resources/index.md)。  
  
6.  編譯和部署您的控制項。  若要編譯和部署 `FirstControl,`，請執行下列步驟。  
  
    1.  儲存下列範例中的程式碼至原始程式檔 \(例如 FirstControl.cs 或 FirstControl.vb\)。  
  
    2.  將原始程式碼編譯成組件 \(Assembly\)，並將它儲存在您應用程式的目錄。  若要達成這點，請從含有原始程式檔的目錄中執行下列命令。  
  
        ```vb  
        vbc /t:library /out:[path to your application's directory]/CustomWinControls.dll /r:System.dll /r:System.Windows.Forms.dll /r:System.Drawing.dll FirstControl.vb  
        ```  
  
        ```csharp  
        csc /t:library /out:[path to your application's directory]/CustomWinControls.dll /r:System.dll /r:System.Windows.Forms.dll /r:System.Drawing.dll FirstControl.cs  
        ```  
  
         `/t:library` 編譯器選項會告訴編譯器，您正在建立的組件是程式庫 \(而不是可執行檔\)。  `/out` 選項指定組件的路徑和名稱。  `/r` 選項會提供您程式碼所參考組件的名稱。  在這個範例中，您建立只有您的應用程式可以使用的私用 \(Private\) 組件。  因此您必須將它儲存於您應用程式的目錄。  如需封裝和部署散發的控制項的詳細資訊，請參閱[部署](../../../../docs/framework/deployment/net-framework-and-applications.md)。  
  
 下列範例示範 `FirstControl` 的程式碼。  控制項被封入在命名空間 `CustomWinControls` 中。  命名空間提供相關型別的邏輯群組。  您可以在新的或現有命名空間中建立您的控制項。  在 C\# 中，`using` 宣告 \(在 Visual Basic 中為 `Imports`\) 允許型別從命名空間來存取，而不需使用型別的完整名稱。  在下列範例中，`using` 宣告允許程式碼僅用 <xref:System.Windows.Forms.Control> 從 <xref:System.Windows.Forms?displayProperty=fullName> 存取 <xref:System.Windows.Forms.Control> 類別，而不必使用完整名稱 <xref:System.Windows.Forms.Control?displayProperty=fullName>。  
  
 [!code-csharp[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
 [!code-vb[System.Windows.Forms.FirstControl#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]  
  
## 在網頁上使用自訂控制項  
 下列範例示範使用 `FirstControl` 的簡單表單。  它建立三個 `FirstControl` 的執行個體，各個都有不同的 `TextAlignment` 屬性值。  
  
#### 編譯和執行這個範例  
  
1.  儲存下列範例中的程式碼至原始程式檔 \(SimpleForm.cs 或 SimpleForms.vb\)。  
  
2.  從含有原始程式檔的目錄執行下列命令，將原始程式碼編譯成可執行組件。  
  
    ```vb  
    vbc /r:CustomWinControls.dll /r:System.dll /r:System.Windows.Forms.dll /r:System.Drawing.dll SimpleForm.vb  
    ```  
  
    ```csharp  
    csc /r:CustomWinControls.dll /r:System.dll /r:System.Windows.Forms.dll /r:System.Drawing.dll SimpleForm.cs  
    ```  
  
     CustomWinControls.dll 為含有類別 `FirstControl` 的組件。  這個組件必須位於存取它的表單 \(SimpleForm.cs 或 SimpleForms.vb\) 的原始程式檔的相同目錄。  
  
3.  使用下列命令執行 SimpleForm.exe。  
  
    ```  
    SimpleForm  
    ```  
  
 [!code-csharp[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
 [!code-vb[System.Windows.Forms.FirstControl#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]  
  
## 請參閱  
 [Windows Form 控制項中的屬性](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)   
 [Windows Form 控制項中的事件](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)