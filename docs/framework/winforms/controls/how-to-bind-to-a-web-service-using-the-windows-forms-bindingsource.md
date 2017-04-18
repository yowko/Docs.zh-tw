---
title: "如何：使用 Windows Form BindingSource 繫結至 Web 服務 | Microsoft Docs"
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
  - "BindingSource 元件 [Windows Form], 繫結至 Web 服務"
  - "BindingSource 元件 [Windows Form], 範例"
  - "控制項 [Windows Form], 繫結至 Web 服務"
  - "範例 [Windows Form], BindingSource 元件"
  - "Web 服務, 繫結控制項"
ms.assetid: ee261207-4573-4cb9-a8cb-5185037e0fba
caps.latest.revision: 26
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 26
---
# 如何：使用 Windows Form BindingSource 繫結至 Web 服務
如果您想要將 Windows Form 控制項繫結至取自呼叫 XML Web service 的結果，您可以使用 <xref:System.Windows.Forms.BindingSource> 元件。  此程序是類似於繫結 <xref:System.Windows.Forms.BindingSource> 元件到一種類型上。  您必須建立用戶端 Proxy，其中包含方法和 Web 服務所公開的類型。  您可以由 Web 服務 \(.asmx\) 本身或它的 Web 服務描述語言 \(WSDL\) 檔案來產生用戶端 Proxy 。  此外，用戶端 Proxy 必須公開欄位，內容為被 Web 服務做為公用屬性的複雜類型。  然後再繫結 <xref:System.Windows.Forms.BindingSource> 到其中一個在 Web 服務 Proxy 中被公開的類型。  
  
### 建立並繫結至用戶端 Proxy  
  
1.  依照您的選擇，以適當的命名空間在目錄中建立 Windows Form。  
  
2.  新增 <xref:System.Windows.Forms.BindingSource> 元件至表單。  
  
3.  開啟 [!INCLUDE[winsdklong](../../../../includes/winsdklong-md.md)] 命令提示字元，並瀏覽至您的表單所位於的相同目錄。  
  
4.  使用 WSDL 工具中，輸入 `wsdl` 以及 .asmx 或者 Web 服務之 WSDL 檔案的 URL ，接著是您的應用程式命名空間，最後可以選擇加上您使用的語言。  
  
     下列程式碼範例所使用的 Web 服務位於 http:\/\/webservices.eraserver.  net\/zipcoderesolver\/zipcoderesolver.asmx。  例如，對於 C\# 類型 `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService` ，或 Visual Basic 類型 `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language: vb`。  在特定的語言中，將路徑當做引數傳遞至 WSDL 工具會產生用戶端 Proxy 於相同的目錄和命名空間中，並做為您的應用程式。  如果您使用 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] ，將檔案加入至您的專案。  
  
5.  在用戶端 Proxy 的類型中選取一個來繫結。  
  
     這通常是由 Web 服務所提供的方法來傳回的類型。  被選取類型的欄位必須公開為公用屬性，以供繫結用途。  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#4)]  
  
6.  設定 <xref:System.Windows.Forms.BindingSource> 中的 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 屬性為您希望被包含在Web 服務用戶端 Proxy 的類型。  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#2)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#2)]  
  
### 將控制項繫結到已繫結至某一 Web 服務的 BindingSource 上  
  
-   將控制項繫結到 <xref:System.Windows.Forms.BindingSource>，傳遞您想要其做為參數的 Web 服務類型之公開屬性。  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#3)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#3)]  
  
## 範例  
 下列程式碼範例將示範如何將 <xref:System.Windows.Forms.BindingSource> 元件繫結 到 Web 服務，接著如何將文字方塊繫結到 <xref:System.Windows.Forms.BindingSource> 元件。  當您按下此按鈕，會呼叫 Web 服務方法並且於 `textbox1` 中顯示結果。  
  
 [!code-cpp[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#1)]  
  
## 編譯程式碼  
 這一個完整的範例，其中包含一個 `Main` 方法以及一個精簡版本的用戶端 Proxy 程式碼。  
  
 這個範例需要：  
  
-   System, System.Drawing、 System.Web.Services、 System.Windows.Forms 以及 System.Xml 組件 的參考。  
  
 如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列來建置本範例的相關資訊，請參閱[從命令列建置](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) 或[使用 csc.exe 建置命令列](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱[如何：使用 Visual Studio 來編譯與執行完整的 Windows Forms 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## 請參閱  
 [BindingSource 元件](../../../../docs/framework/winforms/controls/bindingsource-component.md)   
 [如何：將 Windows Form 控制項繫結至類型](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)