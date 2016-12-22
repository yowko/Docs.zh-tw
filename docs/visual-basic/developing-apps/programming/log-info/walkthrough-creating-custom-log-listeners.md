---
title: "Walkthrough: Creating Custom Log Listeners (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "custom log listeners"
  - "My.Application.Log object, custom log listeners"
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Walkthrough: Creating Custom Log Listeners (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

這個逐步解說會示範如何建立自訂的記錄檔接聽程式，並將它設定為接聽 `My.Application.Log` 物件的輸出。  
  
## 使用者入門  
 記錄檔接聽程式必須繼承自 <xref:System.Diagnostics.TraceListener> 類別。  
  
#### 若要建立接聽程式  
  
-   在應用程式中建立名為 `SimpleListener` 的類別，並使它繼承自 <xref:System.Diagnostics.TraceListener>。  
  
     [!CODE [VbVbalrMyApplicationLog#16](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog#16)]  
  
     基底類別所需的 <xref:System.Diagnostics.TraceListener.Write%2A> 和 <xref:System.Diagnostics.TraceListener.WriteLine%2A> 方法會呼叫 `MsgBox` 顯示輸入。  
  
     <xref:System.Security.Permissions.HostProtectionAttribute> 屬性 \(Attribute\) 則會套用到 <xref:System.Diagnostics.TraceListener.Write%2A> 和 <xref:System.Diagnostics.TraceListener.WriteLine%2A> 方法，使這些方法的屬性符合基底類別方法。  <xref:System.Security.Permissions.HostProtectionAttribute> 屬性可以讓執行程式碼的主應用程式判斷該程式碼是否公開 \(Expose\) 主應用程式同步處理防護。  
  
    > [!NOTE]
    >  <xref:System.Security.Permissions.HostProtectionAttribute> 屬性只有在裝載 Common Language Runtime 以及實作主應用程式防護的 Unmanaged 應用程式 \(例如 SQL Server\) 上才會生效。  
  
 若要確保 `My.Application.Log` 會使用您的記錄檔接聽程式，您應該以強式名稱來命名記錄檔接聽程式所在的組件。  
  
 下面這個程序提供一些簡單的步驟，建立具有強式名稱的記錄檔接聽程式組件。  如需詳細資訊，請參閱[建立和使用強式名稱的組件](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md)。  
  
#### 若要以強式名稱命名記錄檔接聽程式組件  
  
1.  在 \[**方案總管**\] 中選取專案。  在 \[**專案**\] 功能表上，選擇 \[**屬性**\]。  如需詳細資訊，請參閱[Introduction to the Project Designer](http://msdn.microsoft.com/zh-tw/898dd854-c98d-430c-ba1b-a913ce3c73d7)。  
  
2.  按一下 \[**簽署**\] 索引標籤。  
  
3.  選取 \[**簽署組件**\] 方塊。  
  
4.  從 \[**選擇強式名稱金鑰檔**\] 下拉式清單中，選擇 \[**\<新增\>**\]。  
  
     \[**建立強式名稱金鑰**\] 對話方塊隨即開啟。  
  
5.  在 \[**金鑰檔名稱**\] 方塊中提供金鑰檔的名稱。  
  
6.  在 \[**輸入密碼**\] 和 \[**確認密碼**\] 方塊中輸入密碼。  
  
7.  按一下 \[**確定**\]。  
  
8.  重建應用程式。  
  
## 加入接聽程式  
 使組件具有強式名稱後，現在您需要判斷接聽程式的強式名稱，讓 `My.Application.Log` 使用您的記錄檔接聽程式。  
  
 具有強式名稱之型別的格式如下：  
  
 \<型別名稱\>, \<組件名稱\>, \<版本號碼\>, \<文化特性\>, \<強式名稱\>  
  
#### 若要判斷接聽程式的強式名稱  
  
-   下列程式碼會顯示如何判斷 `SimpleListener` 的強式名稱型別名稱。  
  
     [!CODE [VbVbalrMyApplicationLog#17](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog#17)]  
  
     型別的強式名稱視專案而定。  
  
 透過強式名稱，您可以將接聽程式加入至 `My.Application.Log` 記錄檔接聽程式集合。  
  
#### 若要將接聽程式加入至 My.Application.Log  
  
1.  以滑鼠右鍵按一下 \[**方案總管**\] 的 \[app.config\]，並選擇 \[**開啟**\]。  
  
     \-或\-  
  
     如果沒有 app.config 檔：  
  
    1.  在 \[**專案**\] 功能表中，選擇 \[**加入新項目**\]。  
  
    2.  從 \[**加入新項目**\] 對話方塊中選擇 \[**應用程式組態檔**\]。  
  
    3.  按一下 \[**加入**\]。  
  
2.  在具有 `name` 屬性為 "DefaultSource" 的 `<source>` 區段 \(此區段位於 `<sources>` 區段\) 中，尋找 `<listeners>`。  `<sources>` 區段是在最上層 `<configuration>` 區段的 `<system.diagnostics>` 區段中。  
  
3.  將這個項目加入至 `<listeners>` 區段：  
  
    ```  
    <add name="SimpleLog" />  
    ```  
  
4.  在最上層 `<configuration>` 區段的 `<system.diagnostics>` 區段中，尋找 `<sharedListeners>` 區段。  
  
5.  將這個項目加入至此 `<sharedListeners>` 區段：  
  
    ```  
    <add name="SimpleLog" type="SimpleLogStrongName" />  
    ```  
  
     將 `SimpleLogStrongName` 的值變更為接聽程式的強式名稱。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=fullName>   
 [使用應用程式記錄檔](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)   
 [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)   
 [如何：寫入記錄訊息](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)   
 [逐步解說：變更 My.Application.Log 寫入資訊的位置](../Topic/Walkthrough:%20Changing%20Where%20My.Application.Log%20Writes%20Information%20\(Visual%20Basic\).md)