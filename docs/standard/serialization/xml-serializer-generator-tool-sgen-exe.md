---
title: XML 序列化程式產生器工具 (Sgen.exe)
description: XML 序列化程式產生器會針對元件中的類型建立 XML 序列化元件，以改善 XmlSerializer 的啟動效能。
ms.date: 03/30/2017
ms.assetid: cc1d1f1c-fb26-4be9-885a-3fe84c81cec6
ms.openlocfilehash: b6d9406ca6a69f7bdff3129b55c89dd5d1589d3f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288936"
---
# <a name="xml-serializer-generator-tool-sgenexe"></a><span data-ttu-id="caa80-103">XML 序列化程式產生器工具 (Sgen.exe)</span><span class="sxs-lookup"><span data-stu-id="caa80-103">XML Serializer Generator Tool (Sgen.exe)</span></span>

<span data-ttu-id="caa80-104">XML 序列化程式產生器會針對指定元件中的類型建立 XML 序列化元件。</span><span class="sxs-lookup"><span data-stu-id="caa80-104">The XML Serializer Generator creates an XML serialization assembly for types in a specified assembly.</span></span> <span data-ttu-id="caa80-105">序列化元件會在序列化或還原序列化 <xref:System.Xml.Serialization.XmlSerializer> 指定類型的物件時，改善的啟動效能。</span><span class="sxs-lookup"><span data-stu-id="caa80-105">The serialization assembly improves the startup performance of a <xref:System.Xml.Serialization.XmlSerializer> when it serializes or deserializes objects of the specified types.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="caa80-106">語法</span><span class="sxs-lookup"><span data-stu-id="caa80-106">Syntax</span></span>

<span data-ttu-id="caa80-107">從命令列執行工具。</span><span class="sxs-lookup"><span data-stu-id="caa80-107">Run the tool from the command line.</span></span>
  
```console  
sgen [options]  
```
  
> [!TIP]
> <span data-ttu-id="caa80-108">若要讓 .NET Framework 工具正常運作，您必須 `Path` `Include` 正確地設定、和 `Lib` 環境變數。</span><span class="sxs-lookup"><span data-stu-id="caa80-108">For .NET Framework tools to function properly, you must set your `Path`, `Include`, and `Lib` environment variables correctly.</span></span> <span data-ttu-id="caa80-109">藉由執行 SDKVars （位於 \V2.0\Bin 目錄中）來設定這些環境變數 \<SDK> 。</span><span class="sxs-lookup"><span data-stu-id="caa80-109">Set these environment variables by running SDKVars.bat, which is located in the \<SDK>\v2.0\Bin directory.</span></span> <span data-ttu-id="caa80-110">SDKVars.bat 必須在每一個命令提示字元中執行。</span><span class="sxs-lookup"><span data-stu-id="caa80-110">SDKVars.bat must be executed in every command shell.</span></span>
  
## <a name="parameters"></a><span data-ttu-id="caa80-111">參數</span><span class="sxs-lookup"><span data-stu-id="caa80-111">Parameters</span></span>  
  
|<span data-ttu-id="caa80-112">選項</span><span class="sxs-lookup"><span data-stu-id="caa80-112">Option</span></span>|<span data-ttu-id="caa80-113">描述</span><span class="sxs-lookup"><span data-stu-id="caa80-113">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="caa80-114">**/a \[ 元件 s) \] ：**_filename_</span><span class="sxs-lookup"><span data-stu-id="caa80-114">**/a\[ssembly\]:**_filename_</span></span>|<span data-ttu-id="caa80-115">為組件中包含的所有類型或 *filename* 所指定的可執行檔產生序列化程式碼。</span><span class="sxs-lookup"><span data-stu-id="caa80-115">Generates serialization code for all the types contained in the assembly or executable specified by *filename*.</span></span> <span data-ttu-id="caa80-116">只能提供一個檔名。</span><span class="sxs-lookup"><span data-stu-id="caa80-116">Only one file name can be provided.</span></span> <span data-ttu-id="caa80-117">如果重複使用這個引數，則會使用最後一個檔名。</span><span class="sxs-lookup"><span data-stu-id="caa80-117">If this argument is repeated, the last file name is used.</span></span>|  
|<span data-ttu-id="caa80-118">**/c \[ 譯器 \] ：**_選項_</span><span class="sxs-lookup"><span data-stu-id="caa80-118">**/c\[ompiler\]:**_options_</span></span>|<span data-ttu-id="caa80-119">指定要傳遞至 C# 編譯器的選項。</span><span class="sxs-lookup"><span data-stu-id="caa80-119">Specifies the options to pass to the C# compiler.</span></span> <span data-ttu-id="caa80-120">所有 csc.exe 選項都受到支援，可以傳遞至編譯器。</span><span class="sxs-lookup"><span data-stu-id="caa80-120">All csc.exe options are supported as they are passed to the compiler.</span></span> <span data-ttu-id="caa80-121">這個選項可以用來指定組件必須經過簽署，並指定金鑰檔。</span><span class="sxs-lookup"><span data-stu-id="caa80-121">This can be used to specify that the assembly should be signed and to specify the key file.</span></span>|  
|<span data-ttu-id="caa80-122">**/d \[ 偵錯\]**</span><span class="sxs-lookup"><span data-stu-id="caa80-122">**/d\[ebug\]**</span></span>|<span data-ttu-id="caa80-123">產生可以與偵錯工具搭配使用的影像。</span><span class="sxs-lookup"><span data-stu-id="caa80-123">Generates an image that can be used with a debugger.</span></span>|  
|<span data-ttu-id="caa80-124">**/f \[ orce\]**</span><span class="sxs-lookup"><span data-stu-id="caa80-124">**/f\[orce\]**</span></span>|<span data-ttu-id="caa80-125">強制覆寫現有的同名組件。</span><span class="sxs-lookup"><span data-stu-id="caa80-125">Forces the overwriting of an existing assembly of the same name.</span></span> <span data-ttu-id="caa80-126">預設值為 **false**。</span><span class="sxs-lookup"><span data-stu-id="caa80-126">The default is **false**.</span></span>|  
|<span data-ttu-id="caa80-127">**/help 或/？**</span><span class="sxs-lookup"><span data-stu-id="caa80-127">**/help or /?**</span></span>|<span data-ttu-id="caa80-128">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="caa80-128">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="caa80-129">**/k \[ 保留\]**</span><span class="sxs-lookup"><span data-stu-id="caa80-129">**/k\[eep\]**</span></span>|<span data-ttu-id="caa80-130">將產生的原始程式檔 (Source File) 和其他暫存檔案編譯成序列化組件之後，隱藏刪除這些檔案的動作。</span><span class="sxs-lookup"><span data-stu-id="caa80-130">Suppresses the deletion of the generated source files and other temporary files after they have been compiled into the serialization assembly.</span></span> <span data-ttu-id="caa80-131">這個選項可以用來判斷工具是否正在為特定的型別產生序列化程式碼。</span><span class="sxs-lookup"><span data-stu-id="caa80-131">This can be used to determine whether the tool is generating serialization code for a particular type.</span></span>|  
|<span data-ttu-id="caa80-132">**/n \[ ologo\]**</span><span class="sxs-lookup"><span data-stu-id="caa80-132">**/n\[ologo\]**</span></span>|<span data-ttu-id="caa80-133">隱藏顯示 Microsoft 程式啟始資訊。</span><span class="sxs-lookup"><span data-stu-id="caa80-133">Suppresses the display of the Microsoft startup banner.</span></span>|  
|<span data-ttu-id="caa80-134">**/o \[ \] 內容：**_路徑_</span><span class="sxs-lookup"><span data-stu-id="caa80-134">**/o\[ut\]:**_path_</span></span>|<span data-ttu-id="caa80-135">指定要在其中儲存所產生之組件的目錄。</span><span class="sxs-lookup"><span data-stu-id="caa80-135">Specifies the directory in which to save the generated assembly.</span></span> <span data-ttu-id="caa80-136">**注意：** 產生的組件名稱是由輸入組件的名稱加上 "xmlSerializers.dll" 所組成。</span><span class="sxs-lookup"><span data-stu-id="caa80-136">**Note:**  The name of the generated assembly is composed of the name of the input assembly plus "xmlSerializers.dll".</span></span>|  
|<span data-ttu-id="caa80-137">**/p \[ roxytypes\]**</span><span class="sxs-lookup"><span data-stu-id="caa80-137">**/p\[roxytypes\]**</span></span>|<span data-ttu-id="caa80-138">只為 XML Web 服務 Proxy 型別產生序列化程式碼。</span><span class="sxs-lookup"><span data-stu-id="caa80-138">Generates serialization code only for the XML Web service proxy types.</span></span>|  
|<span data-ttu-id="caa80-139">**/r \[ eference \] ：**_assemblyfiles_</span><span class="sxs-lookup"><span data-stu-id="caa80-139">**/r\[eference\]:**_assemblyfiles_</span></span>|<span data-ttu-id="caa80-140">指定要求 XML 序列化的型別所參考的組件。</span><span class="sxs-lookup"><span data-stu-id="caa80-140">Specifies the assemblies that are referenced by the types requiring XML serialization.</span></span> <span data-ttu-id="caa80-141">這個選項接受以逗號分隔多個組件檔案。</span><span class="sxs-lookup"><span data-stu-id="caa80-141">Accepts multiple assembly files separated by commas.</span></span>|  
|<span data-ttu-id="caa80-142">**/s \[ ilent\]**</span><span class="sxs-lookup"><span data-stu-id="caa80-142">**/s\[ilent\]**</span></span>|<span data-ttu-id="caa80-143">隱藏顯示成功訊息。</span><span class="sxs-lookup"><span data-stu-id="caa80-143">Suppresses the display of success messages.</span></span>|  
|<span data-ttu-id="caa80-144">**/t \[ 輸入 \] ：**_類型_</span><span class="sxs-lookup"><span data-stu-id="caa80-144">**/t\[ype\]:**_type_</span></span>|<span data-ttu-id="caa80-145">只為指定的型別產生序列化程式碼。</span><span class="sxs-lookup"><span data-stu-id="caa80-145">Generates serialization code only for the specified type.</span></span>|  
|<span data-ttu-id="caa80-146">**/v \[ erbose\]**</span><span class="sxs-lookup"><span data-stu-id="caa80-146">**/v\[erbose\]**</span></span>|<span data-ttu-id="caa80-147">顯示詳細資訊輸出以供偵錯。</span><span class="sxs-lookup"><span data-stu-id="caa80-147">Displays verbose output for debugging.</span></span> <span data-ttu-id="caa80-148">此選項會列出無法使用 <xref:System.Xml.Serialization.XmlSerializer> 進行序列化之目標組件中的型別。</span><span class="sxs-lookup"><span data-stu-id="caa80-148">Lists types from the target assembly that cannot be serialized with the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|<span data-ttu-id="caa80-149">**/?**</span><span class="sxs-lookup"><span data-stu-id="caa80-149">**/?**</span></span>|<span data-ttu-id="caa80-150">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="caa80-150">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="caa80-151">備註</span><span class="sxs-lookup"><span data-stu-id="caa80-151">Remarks</span></span>  
 <span data-ttu-id="caa80-152">如果未使用 XML 序列化程式產生器，則每當應用程式執行時，<xref:System.Xml.Serialization.XmlSerializer> 便會為每個型別產生序列化程式碼和序列化組件。</span><span class="sxs-lookup"><span data-stu-id="caa80-152">When the XML Serializer Generator is not used, a <xref:System.Xml.Serialization.XmlSerializer> generates serialization code and a serialization assembly for each type every time an application is run.</span></span> <span data-ttu-id="caa80-153">若要改善 XML 序列化啟動的效能，請使用 Sgen 工具來預先產生這些元件。</span><span class="sxs-lookup"><span data-stu-id="caa80-153">To improve the performance of XML serialization startup, use the Sgen.exe tool to generate those assemblies in advance.</span></span> <span data-ttu-id="caa80-154">然後，這些組件便可以與應用程式一起部署。</span><span class="sxs-lookup"><span data-stu-id="caa80-154">These assemblies can then be deployed with the application.</span></span>  
  
 <span data-ttu-id="caa80-155">XML 序列化程式產生器也可以改善用戶端使用 XML Web Service Proxy 與伺服器進行通訊的效能，因為在第一次載入型別時，序列化處理序並不會影響到效能。</span><span class="sxs-lookup"><span data-stu-id="caa80-155">The XML Serializer Generator can also improve the performance of clients that use XML Web service proxies to communicate with servers because the serialization process will not incur a performance hit when the type is loaded the first time.</span></span>  
  
 <span data-ttu-id="caa80-156">這些產生的組件無法在 Web 服務的伺服器端上使用。</span><span class="sxs-lookup"><span data-stu-id="caa80-156">These generated assemblies cannot be used on the server side of a Web service.</span></span> <span data-ttu-id="caa80-157">這個工具只能在 Web 服務用戶端和手動序列化案例中使用。</span><span class="sxs-lookup"><span data-stu-id="caa80-157">This tool is only for Web service clients and manual serialization scenarios.</span></span>  
  
 <span data-ttu-id="caa80-158">如果含有要序列化之型別的組件名稱為 MyType.dll，關聯的序列化組件名稱就會是 MyType.XmlSerializers.dll。</span><span class="sxs-lookup"><span data-stu-id="caa80-158">If the assembly containing the type to serialize is named MyType.dll, then the associated serialization assembly will be named MyType.XmlSerializers.dll.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="caa80-159">範例</span><span class="sxs-lookup"><span data-stu-id="caa80-159">Examples</span></span>  
 <span data-ttu-id="caa80-160">下列命令會建立名為 Data.XmlSerializers.dll 的組件，用以序列化 Data.dll 組件中所包含的所有型別。</span><span class="sxs-lookup"><span data-stu-id="caa80-160">The following command creates an assembly named Data.XmlSerializers.dll for serializing all the types contained in the assembly named Data.dll.</span></span>  
  
```console  
sgen Data.dll
```  
  
 <span data-ttu-id="caa80-161">Data.XmlSerializers.dll 組件可以從程式碼參考，而該程式碼必須序列化及還原序列化 Data.dll 中的型別。</span><span class="sxs-lookup"><span data-stu-id="caa80-161">The Data.XmlSerializers.dll assembly can be referenced from code that needs to serialize and deserialize the types in Data.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caa80-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="caa80-162">See also</span></span>

- [<span data-ttu-id="caa80-163">工具</span><span class="sxs-lookup"><span data-stu-id="caa80-163">Tools</span></span>](../../framework/tools/index.md)
- [<span data-ttu-id="caa80-164">命令提示字元</span><span class="sxs-lookup"><span data-stu-id="caa80-164">Command Prompts</span></span>](../../framework/tools/developer-command-prompt-for-vs.md)
