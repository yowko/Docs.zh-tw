---
title: 以 XmlSerializer 自訂序列化順序
ms.date: 03/30/2017
ms.assetid: 975abd20-2a1d-42db-aed3-e898025ccce7
ms.openlocfilehash: f63d460163c33c4253cf565a5755babc1030164f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295027"
---
# <a name="custom-serialization-order-with-xmlserializer"></a><span data-ttu-id="2ed04-102">以 XmlSerializer 自訂序列化順序</span><span class="sxs-lookup"><span data-stu-id="2ed04-102">Custom Serialization Order With XmlSerializer</span></span>
[<span data-ttu-id="2ed04-103">下載範例</span><span class="sxs-lookup"><span data-stu-id="2ed04-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/CustomOrder.zip.exe)  
  
 <span data-ttu-id="2ed04-104">這個範例會示範如何在 XML 序列化中，控制已序列化及已還原序列化之項目的順序。</span><span class="sxs-lookup"><span data-stu-id="2ed04-104">This sample shows how to control the order of serialized and deserialized elements for XML serialization.</span></span>  
  
 <span data-ttu-id="2ed04-105">如需序列化的詳細資訊，請檢視原始程式碼和 build.proj 檔案中的註解。</span><span class="sxs-lookup"><span data-stu-id="2ed04-105">Review comments in the source code and build.proj files for more information on serialization.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="2ed04-106">若要使用命令提示字元建置範例</span><span class="sxs-lookup"><span data-stu-id="2ed04-106">To build the sample using the Command Prompt</span></span>  
  
1. <span data-ttu-id="2ed04-107">開啟 [命令提示字元] 視窗，並巡覽至此範例的任一程式設計語言的子目錄。</span><span class="sxs-lookup"><span data-stu-id="2ed04-107">Open the Command Prompt window and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2. <span data-ttu-id="2ed04-108">在命令列鍵入 **msbuild CustomOrder.sln**。</span><span class="sxs-lookup"><span data-stu-id="2ed04-108">Type **msbuild CustomOrder.sln** at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="2ed04-109">若要使用 Visual Studio 建置範例</span><span class="sxs-lookup"><span data-stu-id="2ed04-109">To build the sample using Visual Studio</span></span>  
  
1. <span data-ttu-id="2ed04-110">開啟 [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)]，並巡覽至此範例任一程式設計語言的子目錄。</span><span class="sxs-lookup"><span data-stu-id="2ed04-110">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2. <span data-ttu-id="2ed04-111">按兩下 CustomOrder.sln 的圖示，在 Visual Studio 中開啟這個檔案。</span><span class="sxs-lookup"><span data-stu-id="2ed04-111">Double-click the icon for the CustomOrder.sln to open the file in Visual Studio.</span></span>  
  
3. <span data-ttu-id="2ed04-112">在 [建置] 功能表中，選取 [建置方案]。</span><span class="sxs-lookup"><span data-stu-id="2ed04-112">In the **Build** menu, select **Build Solution**.</span></span>  
  
4. <span data-ttu-id="2ed04-113">此範例應用程式將建置於預設的 \bin 或 \bin\Debug 子目錄中。</span><span class="sxs-lookup"><span data-stu-id="2ed04-113">The sample application is built in the default \bin or \bin\Debug subdirectory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ed04-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ed04-114">See also</span></span>

- [<span data-ttu-id="2ed04-115">基本序列化</span><span class="sxs-lookup"><span data-stu-id="2ed04-115">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)
- [<span data-ttu-id="2ed04-116">二進位序列化</span><span class="sxs-lookup"><span data-stu-id="2ed04-116">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)
- [<span data-ttu-id="2ed04-117">使用屬性控制 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="2ed04-117">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)
- [<span data-ttu-id="2ed04-118">XML 序列化簡介</span><span class="sxs-lookup"><span data-stu-id="2ed04-118">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="2ed04-119">序列化</span><span class="sxs-lookup"><span data-stu-id="2ed04-119">Serialization</span></span>](../../../docs/standard/serialization/index.md)
- [<span data-ttu-id="2ed04-120">XML 和 SOAP 序列化</span><span class="sxs-lookup"><span data-stu-id="2ed04-120">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
