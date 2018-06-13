---
title: SchemaImporterExtension 技術範例
ms.date: 03/30/2017
ms.assetid: 3f5eb78f-0ef6-433a-b095-3a63b1ce0bc9
ms.openlocfilehash: 07856c9825785aa7bbc123d0a835e4dc863b8ec6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581351"
---
# <a name="schemaimporterextension-technology-sample"></a><span data-ttu-id="cbf0a-102">SchemaImporterExtension 技術範例</span><span class="sxs-lookup"><span data-stu-id="cbf0a-102">SchemaImporterExtension Technology Sample</span></span>
[<span data-ttu-id="cbf0a-103">下載範例</span><span class="sxs-lookup"><span data-stu-id="cbf0a-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/SchemaImporterExtension.zip.exe)  
  
 <span data-ttu-id="cbf0a-104">這個範例示範了自訂的 <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension>，它能夠在匯入 XML 結構描述時，精細地控制程式碼的產生。</span><span class="sxs-lookup"><span data-stu-id="cbf0a-104">This sample demonstrates a custom <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> that allows fine control over code generation when an XML schema is imported.</span></span> <span data-ttu-id="cbf0a-105">應用程式中會示範如何建置、註冊及叫用 (Invoke) 這個擴充功能。</span><span class="sxs-lookup"><span data-stu-id="cbf0a-105">The application shows how to build, register and invoke this extension.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="cbf0a-106">若要使用命令提示字元建置範例</span><span class="sxs-lookup"><span data-stu-id="cbf0a-106">To build the sample using the command prompt</span></span>  
  
1.  <span data-ttu-id="cbf0a-107">開啟 [命令提示字元] 視窗，並巡覽至此範例任一程式設計語言的子目錄。</span><span class="sxs-lookup"><span data-stu-id="cbf0a-107">Open a Command Prompt window and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="cbf0a-108">在命令列鍵入 **msbuild.exe OrderSchemaImporterExtension.sln**。</span><span class="sxs-lookup"><span data-stu-id="cbf0a-108">Type **msbuild.exe OrderSchemaImporterExtension.sln** at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="cbf0a-109">若要使用 Visual Studio 建置範例</span><span class="sxs-lookup"><span data-stu-id="cbf0a-109">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="cbf0a-110">開啟 [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)]，並巡覽至此範例任一程式設計語言的子目錄。</span><span class="sxs-lookup"><span data-stu-id="cbf0a-110">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="cbf0a-111">按兩下 [OrderSchemaImporterExtension.sln] 的圖示，在 Visual Studio 中開啟這個檔案。</span><span class="sxs-lookup"><span data-stu-id="cbf0a-111">Double-click the icon for OrderSchemaImporterExtension.sln to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="cbf0a-112">在 [ **建置** ] 功能表上，按一下 [ **建置方案**]。</span><span class="sxs-lookup"><span data-stu-id="cbf0a-112">On the **Build** menu, click **Build Solution**.</span></span>  
  
 <span data-ttu-id="cbf0a-113">應用程式便會建置在預設的 \bin 或 \bin\Debug 目錄中。</span><span class="sxs-lookup"><span data-stu-id="cbf0a-113">The application will be built in the default \bin or \bin\Debug directory.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="cbf0a-114">若要執行範例</span><span class="sxs-lookup"><span data-stu-id="cbf0a-114">To run the sample</span></span>  
  
1.  <span data-ttu-id="cbf0a-115">使用 [命令提示字元]，巡覽至包含新可執行檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="cbf0a-115">Navigate to the directory containing the new executable, using the command prompt.</span></span>  
  
2.  <span data-ttu-id="cbf0a-116">在命令列鍵入 **[exe name]**。</span><span class="sxs-lookup"><span data-stu-id="cbf0a-116">Type **[exe name]** at the command line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbf0a-117">備註</span><span class="sxs-lookup"><span data-stu-id="cbf0a-117">Remarks</span></span>  
 <span data-ttu-id="cbf0a-118">如需二進位碼建立和註冊步驟之範例的詳細資訊，請參閱原始程式碼和 build.proj 檔案中的註解。</span><span class="sxs-lookup"><span data-stu-id="cbf0a-118">For more information about sample binary creation and registration steps, see the comments in the source code and build.proj files.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbf0a-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbf0a-119">See Also</span></span>  
 <xref:System.CodeDom.CodeCompileUnit>  
 <xref:System.CodeDom.CodeNamespace>  
 <xref:System.CodeDom.CodeNamespaceImport>  
 <xref:Microsoft.CSharp.CSharpCodeProvider>  
 <xref:System.Xml.Serialization.IXmlSerializable>  
 <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension>  
 <xref:System.CodeDom>  
 <xref:System.CodeDom.Compiler>  
 <xref:System.Web.Services.Description>  
 <xref:System.Web.Services.Discovery>  
 <xref:System.Xml.Serialization>  
 <xref:System.Uri>  
 <xref:Microsoft.VisualBasic.VBCodeProvider>  
 <xref:System.Web.Services.Description.WebReference>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>
