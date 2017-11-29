---
title: "如何：使用 Windows Form BindingSource 繫結至 Web 服務"
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
- Web services [Windows Forms], binding controls
- BindingSource component [Windows Forms], binding to a Web service
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to Web service
- BindingSource component [Windows Forms], examples
ms.assetid: ee261207-4573-4cb9-a8cb-5185037e0fba
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d5024ad9000811aa438183de240c91b659644a7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource"></a><span data-ttu-id="f5ffe-102">如何：使用 Windows Form BindingSource 繫結至 Web 服務</span><span class="sxs-lookup"><span data-stu-id="f5ffe-102">How to: Bind to a Web Service Using the Windows Forms BindingSource</span></span>
<span data-ttu-id="f5ffe-103">如果您想要將 Windows Form 控制項繫結至取自呼叫 XML Web service 的結果，您可以使用 <xref:System.Windows.Forms.BindingSource> 元件。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-103">If you want to bind a Windows Form control to the results obtained from calling an XML Web service, you can use a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="f5ffe-104">此程序是類似於繫結 <xref:System.Windows.Forms.BindingSource> 元件到一種類型上。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-104">This procedure is similar to binding a <xref:System.Windows.Forms.BindingSource> component to a type.</span></span> <span data-ttu-id="f5ffe-105">您必須建立用戶端 Proxy，其中包含方法和 Web 服務所公開的類型。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-105">You must create a client-side proxy that contains the methods and types exposed by the Web service.</span></span> <span data-ttu-id="f5ffe-106">您可以由 Web 服務 (.asmx) 本身或它的 Web 服務描述語言 (WSDL) 檔案來產生用戶端 Proxy 。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-106">You generate a client-side proxy from the Web service (.asmx) itself, or its Web Services Description Language (WSDL) file.</span></span> <span data-ttu-id="f5ffe-107">此外，用戶端 Proxy 必須公開欄位，內容為被 Web 服務做為公用屬性的複雜類型。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-107">Additionally, your client-side proxy must expose the fields of complex types used by the Web service as public properties.</span></span> <span data-ttu-id="f5ffe-108">然後再繫結 <xref:System.Windows.Forms.BindingSource> 到其中一個在 Web 服務 Proxy 中被公開的類型。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-108">You then bind the <xref:System.Windows.Forms.BindingSource> to one of the types exposed in the Web service proxy.</span></span>  
  
### <a name="to-create-and-bind-to-a-client-side-proxy"></a><span data-ttu-id="f5ffe-109">建立並繫結至用戶端 Proxy</span><span class="sxs-lookup"><span data-stu-id="f5ffe-109">To create and bind to a client-side proxy</span></span>  
  
1.  <span data-ttu-id="f5ffe-110">依照您的選擇，以適當的命名空間在目錄中建立 Windows Form。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-110">Create a Windows Form in the directory of your choice, with an appropriate namespace.</span></span>  
  
2.  <span data-ttu-id="f5ffe-111">新增 <xref:System.Windows.Forms.BindingSource> 元件至表單。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-111">Add a <xref:System.Windows.Forms.BindingSource> component to the form.</span></span>  
  
3.  <span data-ttu-id="f5ffe-112">開啟 [!INCLUDE[winsdklong](../../../../includes/winsdklong-md.md)] 命令提示字元，並瀏覽至您的表單所位於的相同目錄。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-112">Open the [!INCLUDE[winsdklong](../../../../includes/winsdklong-md.md)] command prompt, and navigate to the same directory that your form is located in.</span></span>  
  
4.  <span data-ttu-id="f5ffe-113">使用 WSDL 工具中，輸入 `wsdl` 以及 .asmx 或者 Web 服務之 WSDL 檔案的 URL，接著是您的應用程式命名空間，最後可以選擇加上您使用的語言。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-113">Using the WSDL tool, enter `wsdl` and the URL for the .asmx or WSDL file for the Web service, followed by the namespace of your application, and optionally the language you are working in.</span></span>  
  
     <span data-ttu-id="f5ffe-114">下列程式碼範例所使用的 Web 服務位於 http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-114">The following code example uses the Web service located at http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx.</span></span> <span data-ttu-id="f5ffe-115">例如，針對 C# 輸入 `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`，或針對 Visual Basic 輸入 `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-115">For example, for C# type `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`, or for Visual Basic type `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`.</span></span> <span data-ttu-id="f5ffe-116">在特定的語言中，將路徑當做引數傳遞至 WSDL 工具會產生用戶端 Proxy 於相同的目錄和命名空間中，並做為您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-116">Passing the path as an argument to the WSDL tool will generate a client-side proxy in the same directory and namespace as your application, in the specified language.</span></span> <span data-ttu-id="f5ffe-117">如果您使用 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] ，將檔案加入至您的專案。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-117">If you are using [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], add the file to your project.</span></span>  
  
5.  <span data-ttu-id="f5ffe-118">在用戶端 Proxy 的類型中選取一個來繫結。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-118">Select a type in the client-side proxy to bind to.</span></span>  
  
     <span data-ttu-id="f5ffe-119">這通常是由 Web 服務所提供的方法來傳回的類型。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-119">This is typically a type returned by a method offered by the Web service.</span></span> <span data-ttu-id="f5ffe-120">被選取類型的欄位必須公開為公用屬性，以供繫結用途。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-120">The fields of the chosen type must be exposed as public properties for binding purposes.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#4)]  
  
6.  <span data-ttu-id="f5ffe-121">設定 <xref:System.Windows.Forms.BindingSource> 中的 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 屬性為您希望被包含在Web 服務用戶端 Proxy 的類型。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-121">Set the <xref:System.Windows.Forms.BindingSource.DataSource%2A> property of the <xref:System.Windows.Forms.BindingSource> to the type you want that is contained in the Web service client-side proxy.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#2)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#2)]  
  
### <a name="to-bind-controls-to-the-bindingsource-that-is-bound-to-a-web-service"></a><span data-ttu-id="f5ffe-122">將控制項繫結到已繫結至某一 Web 服務的 BindingSource 上</span><span class="sxs-lookup"><span data-stu-id="f5ffe-122">To bind controls to the BindingSource that is bound to a Web service</span></span>  
  
-   <span data-ttu-id="f5ffe-123">將控制項繫結到 <xref:System.Windows.Forms.BindingSource>，傳遞您想要其做為參數的 Web 服務類型之公開屬性。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-123">Bind controls to the <xref:System.Windows.Forms.BindingSource>, passing the public property of the Web service type that you want as a parameter.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#3)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="f5ffe-124">範例</span><span class="sxs-lookup"><span data-stu-id="f5ffe-124">Example</span></span>  
 <span data-ttu-id="f5ffe-125">下列程式碼範例將示範如何將 <xref:System.Windows.Forms.BindingSource> 元件繫結 到 Web 服務，接著如何將文字方塊繫結到 <xref:System.Windows.Forms.BindingSource> 元件。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-125">The following code example demonstrates how to bind a <xref:System.Windows.Forms.BindingSource> component to a Web service, and then how to bind a text box to the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="f5ffe-126">當您按下此按鈕，會呼叫 Web 服務方法並且於 `textbox1` 中顯示結果。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-126">When you click the button, a Web service method is called and the results will appear in `textbox1`.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorWebService#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f5ffe-127">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="f5ffe-127">Compiling the Code</span></span>  
 <span data-ttu-id="f5ffe-128">這一個完整的範例，其中包含一個 `Main` 方法以及一個精簡版本的用戶端 Proxy 程式碼。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-128">This is a complete example that includes a `Main` method, and a shortened version of client-side proxy code.</span></span>  
  
 <span data-ttu-id="f5ffe-129">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="f5ffe-129">This example requires:</span></span>  
  
-   <span data-ttu-id="f5ffe-130">System, System.Drawing、 System.Web.Services、 System.Windows.Forms 以及 System.Xml 組件 的參考。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-130">References to the System, System.Drawing, System.Web.Services, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="f5ffe-131">如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置命令列](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-131">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="f5ffe-132">您也可以將程式碼貼在新的專案中，以在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-132">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="f5ffe-133">另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Forms 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="f5ffe-133">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5ffe-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5ffe-134">See Also</span></span>  
 [<span data-ttu-id="f5ffe-135">BindingSource 元件</span><span class="sxs-lookup"><span data-stu-id="f5ffe-135">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="f5ffe-136">操作說明：將 Windows Forms 控制項繫結至型別</span><span class="sxs-lookup"><span data-stu-id="f5ffe-136">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
