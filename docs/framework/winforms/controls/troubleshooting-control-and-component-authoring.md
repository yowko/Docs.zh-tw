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
ms.openlocfilehash: 6494a154b9b4bd5bf29fc0e2fbd0b4e5e84550ff
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364172"
---
# <a name="troubleshooting-control-and-component-authoring"></a>控制項和元件撰寫疑難排解
本主題列出當開發元件和控制項時，會發生下列常見問題。 如需詳細資訊，請參閱[使用元件進行程式設計](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120))。  
  
- 無法將控制項新增至工具箱  
  
- 無法針對 Windows Forms 使用者控制項或元件進行偵錯  
  
- 事件在繼承的控制項或元件中引發兩次  
  
- 設計階段錯誤:「無法建立元件 '*元件名稱*'」  
  
- STAThreadAttribute  
  
- 元件圖示不會出現在工具箱中  
  
## <a name="cannot-add-control-to-toolbox"></a>無法將控制項新增至工具箱  
 如果您想要將您在另一個專案中建立的自訂控制項或協力廠商控制項新增至 [工具箱]  ，您必須手動進行。 如果目前專案包含您的控制項或元件，它應該會自動出現在 [工具箱]  。 如需詳細資訊，請參閱[逐步解說：自動將自訂群組件](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)填入工具箱。  
  
#### <a name="to-add-a-control-to-the-toolbox"></a>將控制項新增至工具箱  
  
1. 以滑鼠右鍵按一下 [工具箱]  ，然後從捷徑功能表選取 [選擇項目]  。  
  
2. 在 [選擇工具箱項目]  對話方塊中，新增元件：  
  
    - 如果您想要新增 .NET Framework 元件或控制項，請按一下 [.NET Framework 元件]  索引標籤。  
  
         -或-  
  
    - 如果您想要新增 COM 元件或 ActiveX 控制項，請按一下 [COM 元件]  索引標籤。  
  
3. 如果您的控制項列在對話方塊中，確認它已選取，然後按一下 [確定]  。  
  
     控制項隨即新增至 [工具箱]  。  
  
4. 如果您的控制項未列在對話方塊中，請執行下列作業︰  
  
    1. 按一下 [瀏覽]  按鈕。  
  
    2. 瀏覽至包含 .dll 檔案 (包含您的控制項) 的資料夾。  
  
    3. 選取 .dll 檔案，然後按一下 [開啟]  。  
  
         您的控制項會出現在對話方塊中。  
  
    4. 確認已選取您的控制項，然後按一下 [確定]  。  
  
         您的控制項隨即新增至 [工具箱]  。  
  
## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a>無法針對 Windows Forms 使用者控制項或元件進行偵錯  
 如果您的<xref:System.Windows.Forms.UserControl>控制項衍生自類別, 您可以使用測試容器來對其執行時間行為進行偵錯工具。 如需詳細資訊，請參閱[如何：測試 UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)的執行時間行為。  
  
 其他自訂控制項和元件不是獨立的專案。 它們必須由 Windows Forms 專案之類的應用程式裝載。 若要針對控制項或元件進行偵錯，您必須將它新增至 Windows Forms 專案。  
  
#### <a name="to-debug-a-control-or-component"></a>針對控制項或元件進行偵錯  
  
1. 按一下 [建置]  功能表上的 [建置方案]  以建置解決方案。  
  
2. 從 [檔案]  功能表，選擇 [新增]  ，然後選擇 [新增專案]  ，以將測試專案新增至您的應用程式。  
  
3. 在 [加入新的專案]  對話方塊中，針對專案型別選擇 [Windows 應用程式]  。  
  
4. 在 [方案總管]  中，以滑鼠右鍵按一下新專案的 [參考]  節點。 在捷徑功能表上，按一下 [加入參考]  以將參考新增至包含控制項或元件的專案。  
  
5. 在測試專案中建立您的控制項或元件的執行個體。 如果您的元件位於 [工具箱]  ，您可以將它拖曳至設計工具介面，或者您可以程式設計方式建立執行個體，如下列程式碼範例所示。  
  
    ```vb  
    Dim Component1 As New MyNeatComponent()  
    ```  
  
    ```csharp  
    MyNeatComponent Component1 = new MyNeatComponent();  
    ```  
  
     您現在可以如同往常一般針對您的控制項或元件進行偵錯。  
  
 如需有關偵錯工具的詳細資訊, 請參閱[ [Visual Studio 中的調試](/visualstudio/debugger/debugging-in-visual-studio)程式和逐步解說:在設計階段時](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md), 對自訂 Windows Forms 控制項進行調試。  
  
## <a name="event-is-raised-twice-in-inherited-control-or-component"></a>事件在繼承的控制項或元件中引發兩次  
 這可能是因為重複的 `Handles` 子句。 如需詳細資訊，請參閱 [Visual Basic 中的繼承事件處理常式疑難排解](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)。  
  
## <a name="design-time-error-failed-to-create-component-component-name"></a>設計階段錯誤:「無法建立元件 ' 元件名稱 '」  
 您的元件或控制項必須提供沒有參數的無參數的處理常式。 當設計環境建立元件或控制項的執行個體時，它不會嘗試提供任何參數給採用參數的建構函式多載。  
  
## <a name="stathreadattribute"></a>STAThreadAttribute  
 會<xref:System.STAThreadAttribute>通知 common language runtime (CLR), Windows Forms 使用單一執行緒的單元模型。 如果您未將此屬性套用至 Windows Forms 應用程式的 `Main` 方法，您可能會發現非預期的行為。 例如, 之類<xref:System.Windows.Forms.ListView>的控制項可能不會出現背景影像。 某些控制項可能也需要此屬性，才能有正確的 AutoComplete 和拖放行為。  
  
## <a name="component-icon-does-not-appear-in-toolbox"></a>元件圖示不會出現在工具箱中  
 當您使用<xref:System.Drawing.ToolboxBitmapAttribute>來建立圖示與自訂群組件的關聯時, 該點陣圖不會出現在自動產生之元件的 [工具箱] 中。 若要查看點陣圖，請使用 [選擇工具箱項目]  對話方塊，重新載入控制項。 如需詳細資訊，請參閱[如何：提供控制項](how-to-provide-a-toolbox-bitmap-for-a-control.md)的 [工具箱] 點陣圖。  
  
## <a name="see-also"></a>另請參閱

- [在設計階段開發 Windows Forms 控制項](developing-windows-forms-controls-at-design-time.md)
- [逐步解說：使用自訂群組件自動填入工具箱](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
- [如何：測試 UserControl 的執行時間行為](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [逐步解說：在設計階段針對自訂 Windows Forms 控制項進行偵錯](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)
- [元件撰寫](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/5dya64wy(v=vs.120))
- [設計階段開發疑難排解](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))
