---
title: ConfigurationCodeGenerator
ms.date: 03/30/2017
ms.assetid: 3913aae8-165f-4014-9262-7fe426f90cb2
ms.openlocfilehash: f12fae48f1cee198aac22e6f09e616b407b4e9b5
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70990058"
---
# <a name="configurationcodegenerator"></a><span data-ttu-id="60678-102">ConfigurationCodeGenerator</span><span class="sxs-lookup"><span data-stu-id="60678-102">ConfigurationCodeGenerator</span></span>
<span data-ttu-id="60678-103">ConfigurationCodeGenerator 是可供您用來公開自訂通道實作給組態系統的工具。</span><span class="sxs-lookup"><span data-stu-id="60678-103">The ConfigurationCodeGenerator is a tool that you can use to expose your custom channel implementations to the configuration system.</span></span> <span data-ttu-id="60678-104">這將允許您的自訂通道使用者使用 .config 檔案設定通道，就像平常使用 `NetTcpBinding` 來設定系統提供的繫結 (例如 `TcpTransportBindingElement`) 或自訂繫結一般。</span><span class="sxs-lookup"><span data-stu-id="60678-104">This allows users of your custom channel to configure your channel by using a .config file just as they would configure a system-provided binding such as `NetTcpBinding` or a custom binding using the `TcpTransportBindingElement`.</span></span>  
  
 <span data-ttu-id="60678-105">使用新的 `BindingElement` 或 `Binding` 撰寫自訂通道並將它公開給程式設計模型時，您必須建立一組類別，讓 `BindingElement` 或 `Binding` 可透過使用 .config 檔案來加以設定。</span><span class="sxs-lookup"><span data-stu-id="60678-105">When you write a custom channel and expose it to the programming model by using a new `BindingElement` or `Binding`, you must create a set of classes to make the `BindingElement` or `Binding` configurable using a .config file.</span></span> <span data-ttu-id="60678-106">您可以使用 ConfigurationCodeGenerator 工具產生這些類別，並增進客戶的使用體驗。</span><span class="sxs-lookup"><span data-stu-id="60678-106">You can use the ConfigurationCodeGenerator tool to generate these classes and enhance your customer's experience.</span></span>  
  
### <a name="to-build-the-tool"></a><span data-ttu-id="60678-107">建置工具</span><span class="sxs-lookup"><span data-stu-id="60678-107">To build the tool</span></span>  
  
1. <span data-ttu-id="60678-108">若要建立方案，請依照[建立 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示進行。</span><span class="sxs-lookup"><span data-stu-id="60678-108">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="60678-109">建立解決方案會產生一個檔案：ConfigurationCodeGenerator .exe。</span><span class="sxs-lookup"><span data-stu-id="60678-109">Building the solution generates one file: ConfigurationCodeGenerator.exe.</span></span> <span data-ttu-id="60678-110">檔案 samplerun.cmd 包含範例命令列，說明如何使用此工具來產生[傳輸的類別：UDP](../../../../docs/framework/wcf/samples/transport-udp.md)範例。</span><span class="sxs-lookup"><span data-stu-id="60678-110">The file SampleRun.cmd has a sample command line that shows how to use this tool to generate the classes for the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>  
  
### <a name="to-run-the-tool"></a><span data-ttu-id="60678-111">執行工具</span><span class="sxs-lookup"><span data-stu-id="60678-111">To run the tool</span></span>  
  
1. <span data-ttu-id="60678-112">如果您同時有自訂 `BindingElement` 型別和自訂 `Binding` 型別，請在命令提示字元中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="60678-112">At the command prompt type the following if you have both a custom `BindingElement` type and a custom `Binding` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereTheseTypesAreDefined  
    ```  
  
     <span data-ttu-id="60678-113">如果您只有自訂 `BindingElement` 型別，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="60678-113">Or type the following if you have only a custom `BindingElement` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /be:YourCustomBindingElementTypeName /dll: TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="60678-114">如果您只有自訂 `Binding` 型別，請輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="60678-114">Or type the following if you have only a custom `Binding` type:</span></span>  
  
    ```console  
    ConfigurationCodeGenerator.exe /sb:YourCustomStdBindingTypeName /dll:TheAssemblyWhereThisTypeIsDefined  
    ```  
  
     <span data-ttu-id="60678-115">命令會產生 `BindingElement` 所需的三個 .cs 檔案 (如果指定 /be: 選項)、標準 `Binding` 所需的五個 .cs 檔案 (如果指定 /sb: 選項) 以及 .xml 檔案。</span><span class="sxs-lookup"><span data-stu-id="60678-115">The command generates three .cs files for the `BindingElement` (if you specified the /be: option), five .cs files for the standard `Binding` (if you specified the /sb: option), and a .xml file.</span></span>  
  
    1. <span data-ttu-id="60678-116">如果使用 /be 選項，則其中一個 .cs 檔案會為您的繫結項目實作 `BindingElementExtensionSection`。</span><span class="sxs-lookup"><span data-stu-id="60678-116">If you used the /be option, one of the .cs files implements the `BindingElementExtensionSection` for your binding element.</span></span> <span data-ttu-id="60678-117">這個程式碼會公開 `BindingElement` 給組態系統，讓其他自訂繫結程序可以使用您的繫結程序項目。</span><span class="sxs-lookup"><span data-stu-id="60678-117">This code exposes your `BindingElement` to the configuration system, so that other custom bindings can use your binding element.</span></span> <span data-ttu-id="60678-118">其他檔案含有表示預設值和常數的類別。</span><span class="sxs-lookup"><span data-stu-id="60678-118">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="60678-119">檔案中會有 `//TODO` 註解，用意在提醒您更新預設值。</span><span class="sxs-lookup"><span data-stu-id="60678-119">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
    2. <span data-ttu-id="60678-120">如果您指定 /sb 選項，其中兩個 .cs 檔案將會分別實作 `StandardBindingElement` 和 `StandardBindingCollectionElement`，藉以向組態系統公開您的標準繫結。</span><span class="sxs-lookup"><span data-stu-id="60678-120">If you specified the /sb option, two of the .cs files implement a `StandardBindingElement` and a `StandardBindingCollectionElement` respectively, which exposes your standard binding to the configuration system.</span></span> <span data-ttu-id="60678-121">其他檔案含有表示預設值和常數的類別。</span><span class="sxs-lookup"><span data-stu-id="60678-121">The other files have classes that represent defaults and constants.</span></span> <span data-ttu-id="60678-122">檔案中會有 `//TODO` 註解，用意在提醒您更新預設值。</span><span class="sxs-lookup"><span data-stu-id="60678-122">The files have `//TODO` comments to remind you to update the default values.</span></span>  
  
         <span data-ttu-id="60678-123">如果您指定了/sb：選項，codetoaddto<\< *YourStdBinding*> .cs 就會有程式碼，您必須手動將其加入至執行標準系結的類別。</span><span class="sxs-lookup"><span data-stu-id="60678-123">If you specified the /sb: option the CodeToAddTo\<*YourStdBinding*>.cs has code that you must manually add into the class that implements your standard binding.</span></span>  
  
     <span data-ttu-id="60678-124">SampleConfig.xml 檔案中含有組態程式碼，您必須將它新增至註冊處理常式 (在前面步驟 1 或 2 中定義) 的組態檔中。</span><span class="sxs-lookup"><span data-stu-id="60678-124">The SampleConfig.xml file contains the configuration code that you must add to the configuration file that registers the handlers defined in the previous step 1 or 2.</span></span>  
