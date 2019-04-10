---
title: 控制項和元件撰寫疑難排解
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- troubleshooting components
- troubleshooting controls [Windows Forms]
- controls [Windows Forms], troubleshooting
- components [Windows Forms], troubleshooting
- Windows Forms controls, debugging
ms.assetid: e9c8c099-2271-4737-882f-50f336c7a55e
ms.openlocfilehash: 3ae8a889bf69913d234e31804335ddb08560c30c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343411"
---
# <a name="troubleshooting-control-and-component-authoring"></a>控制項和元件撰寫疑難排解
本主題列出當開發元件和控制項時，會發生下列常見問題。 如需詳細資訊，請參閱[使用元件進行程式設計](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120))。  
  
-   無法將控制項新增至工具箱  
  
-   無法針對 Windows Forms 使用者控制項或元件進行偵錯  
  
-   事件在繼承的控制項或元件中引發兩次  
  
-   設計階段錯誤：「 無法建立元件 '*元件名稱*' 」  
  
-   STAThreadAttribute  
  
-   元件圖示不會出現在工具箱中  
  
## <a name="cannot-add-control-to-toolbox"></a>無法將控制項新增至工具箱  
 如果您想要將您在另一個專案中建立的自訂控制項或協力廠商控制項新增至 [工具箱]，您必須手動進行。 如果目前專案包含您的控制項或元件，它應該會自動出現在 [工具箱]。 如需詳細資訊，請參閱[逐步解說：自動將 [工具箱] 中的以自訂元件填入](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)。  
  
#### <a name="to-add-a-control-to-the-toolbox"></a>將控制項新增至工具箱  
  
1. 以滑鼠右鍵按一下 [工具箱]，然後從捷徑功能表選取 [選擇項目]。  
  
2. 在 [選擇工具箱項目] 對話方塊中，新增元件：  
  
    -   如果您想要新增 .NET Framework 元件或控制項，請按一下 [.NET Framework 元件] 索引標籤。  
  
         -或-  
  
    -   如果您想要新增 COM 元件或 ActiveX 控制項，請按一下 [COM 元件] 索引標籤。  
  
3. 如果您的控制項列在對話方塊中，確認它已選取，然後按一下 [確定]。  
  
     控制項隨即新增至 [工具箱]。  
  
4. 如果您的控制項未列在對話方塊中，請執行下列作業︰  
  
    1.  按一下 [瀏覽] 按鈕。  
  
    2.  瀏覽至包含 .dll 檔案 (包含您的控制項) 的資料夾。  
  
    3.  選取 .dll 檔案，然後按一下 [開啟]。  
  
         您的控制項會出現在對話方塊中。  
  
    4.  確認已選取您的控制項，然後按一下 [確定]。  
  
         您的控制項隨即新增至 [工具箱]。  
  
## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a>無法針對 Windows Forms 使用者控制項或元件進行偵錯  
 如果您的控制項是衍生自<xref:System.Windows.Forms.UserControl>類別，您可以偵錯與測試容器及其執行階段行為。 如需詳細資訊，請參閱[如何：測試 UserControl 的執行階段行為](how-to-test-the-run-time-behavior-of-a-usercontrol.md)。  
  
 其他自訂控制項和元件不是獨立的專案。 它們必須由 Windows Forms 專案之類的應用程式裝載。 若要針對控制項或元件進行偵錯，您必須將它新增至 Windows Forms 專案。  
  
#### <a name="to-debug-a-control-or-component"></a>針對控制項或元件進行偵錯  
  
1. 按一下 [建置] 功能表上的 [建置方案] 以建置解決方案。  
  
2. 從 [檔案]功能表，選擇 [新增]，然後選擇 [新增專案]，以將測試專案新增至您的應用程式。  
  
3. 在 [加入新的專案] 對話方塊中，針對專案型別選擇 [Windows 應用程式]。  
  
4. 在 [方案總管] 中，以滑鼠右鍵按一下新專案的 [參考] 節點。 在捷徑功能表上，按一下 [加入參考]  以將參考新增至包含控制項或元件的專案。  
  
5. 在測試專案中建立您的控制項或元件的執行個體。 如果您的元件位於 [工具箱]，您可以將它拖曳至設計工具介面，或者您可以程式設計方式建立執行個體，如下列程式碼範例所示。  
  
    ```vb  
    Dim Component1 As New MyNeatComponent()  
    ```  
  
    ```csharp  
    MyNeatComponent Component1 = new MyNeatComponent();  
    ```  
  
     您現在可以如同往常一般針對您的控制項或元件進行偵錯。  
  
 如需有關偵錯的詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中偵錯](/visualstudio/debugger/debugging-in-visual-studio)和[逐步解說：在設計階段偵錯自訂的 Windows Form 控制項](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)。  
  
## <a name="event-is-raised-twice-in-inherited-control-or-component"></a>事件在繼承的控制項或元件中引發兩次  
 這可能是因為重複的 `Handles` 子句。 如需詳細資訊，請參閱 [Visual Basic 中的繼承事件處理常式疑難排解](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)。  
  
## <a name="design-time-error-failed-to-create-component-component-name"></a>設計階段錯誤：「 無法建立元件 '元件名稱' 」  
 您的元件或控制項必須提供沒有參數的預設建構函式。 當設計環境建立元件或控制項的執行個體時，它不會嘗試提供任何參數給採用參數的建構函式多載。  
  
## <a name="stathreadattribute"></a>STAThreadAttribute  
 <xref:System.STAThreadAttribute>通知 common language runtime (CLR)，Windows Form 會使用單一執行緒 apartment 模型。 如果您未將此屬性套用至 Windows Forms 應用程式的 `Main` 方法，您可能會發現非預期的行為。 例如，背景映像可能不會出現的控制項，例如<xref:System.Windows.Forms.ListView>。 某些控制項可能也需要此屬性，才能有正確的 AutoComplete 和拖放行為。  
  
## <a name="component-icon-does-not-appear-in-toolbox"></a>元件圖示不會出現在工具箱中  
 當您使用<xref:System.Drawing.ToolboxBitmapAttribute>来關聯圖示與您的自訂元件，點陣圖不會出現在工具箱中自動產生元件。 若要查看點陣圖，請使用 [選擇工具箱項目] 對話方塊，重新載入控制項。 如需詳細資訊，請參閱[如何：為控制項提供工具箱點陣圖](how-to-provide-a-toolbox-bitmap-for-a-control.md)。  
  
## <a name="see-also"></a>另請參閱

- [在設計階段開發 Windows Form 控制項](developing-windows-forms-controls-at-design-time.md)
- [逐步解說：自動將自訂元件填入工具箱](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [HOW TO：測試 UserControl 的執行階段行為](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [逐步解說：在設計階段偵錯自訂 Windows Forms 控制項](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)
- [元件撰寫](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/5dya64wy(v=vs.120))
- [設計階段開發疑難排解](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))
