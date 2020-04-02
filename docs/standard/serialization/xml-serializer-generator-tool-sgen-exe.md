---
title: XML 序列化程式產生器工具 (Sgen.exe)
ms.date: 03/30/2017
ms.assetid: cc1d1f1c-fb26-4be9-885a-3fe84c81cec6
ms.openlocfilehash: bc1a0abaeef9a9244aa83941e590063c7ef167d1
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588368"
---
# <a name="xml-serializer-generator-tool-sgenexe"></a><span data-ttu-id="05daf-102">XML 序列化程式產生器工具 (Sgen.exe)</span><span class="sxs-lookup"><span data-stu-id="05daf-102">XML Serializer Generator Tool (Sgen.exe)</span></span>

<span data-ttu-id="05daf-103">XML 序列化器產生器為指定程式集中的類型創建 XML 序列化程式集。</span><span class="sxs-lookup"><span data-stu-id="05daf-103">The XML Serializer Generator creates an XML serialization assembly for types in a specified assembly.</span></span> <span data-ttu-id="05daf-104">序列化程式集在序列化或取消序列化<xref:System.Xml.Serialization.XmlSerializer>指定類型的物件時提高了 啟動性能。</span><span class="sxs-lookup"><span data-stu-id="05daf-104">The serialization assembly improves the startup performance of a <xref:System.Xml.Serialization.XmlSerializer> when it serializes or deserializes objects of the specified types.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="05daf-105">語法</span><span class="sxs-lookup"><span data-stu-id="05daf-105">Syntax</span></span>

<span data-ttu-id="05daf-106">從命令行運行該工具。</span><span class="sxs-lookup"><span data-stu-id="05daf-106">Run the tool from the command line.</span></span>
  
```console  
sgen [options]  
```
  
> [!TIP]
> <span data-ttu-id="05daf-107">對於 .NET 框架工具要正常運行,必須`Path``Include`正確`Lib`設置、和環境變數。</span><span class="sxs-lookup"><span data-stu-id="05daf-107">For .NET Framework tools to function properly, you must set your `Path`, `Include`, and `Lib` environment variables correctly.</span></span> <span data-ttu-id="05daf-108">執行位於 \<SDK>\v2.0\Bin 目錄中的 SDKVars.bat，即可設定這些環境變數。</span><span class="sxs-lookup"><span data-stu-id="05daf-108">Set these environment variables by running SDKVars.bat, which is located in the \<SDK>\v2.0\Bin directory.</span></span> <span data-ttu-id="05daf-109">SDKVars.bat 必須在每一個命令提示字元中執行。</span><span class="sxs-lookup"><span data-stu-id="05daf-109">SDKVars.bat must be executed in every command shell.</span></span>
  
## <a name="parameters"></a><span data-ttu-id="05daf-110">參數</span><span class="sxs-lookup"><span data-stu-id="05daf-110">Parameters</span></span>  
  
|<span data-ttu-id="05daf-111">選項</span><span class="sxs-lookup"><span data-stu-id="05daf-111">Option</span></span>|<span data-ttu-id="05daf-112">描述</span><span class="sxs-lookup"><span data-stu-id="05daf-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="05daf-113">**/ssembly\[\]:**_檔案名稱_</span><span class="sxs-lookup"><span data-stu-id="05daf-113">**/a\[ssembly\]:**_filename_</span></span>|<span data-ttu-id="05daf-114">為組件中包含的所有類型或 *filename* 所指定的可執行檔產生序列化程式碼。</span><span class="sxs-lookup"><span data-stu-id="05daf-114">Generates serialization code for all the types contained in the assembly or executable specified by *filename*.</span></span> <span data-ttu-id="05daf-115">只能提供一個檔名。</span><span class="sxs-lookup"><span data-stu-id="05daf-115">Only one file name can be provided.</span></span> <span data-ttu-id="05daf-116">如果重複使用這個引數，則會使用最後一個檔名。</span><span class="sxs-lookup"><span data-stu-id="05daf-116">If this argument is repeated, the last file name is used.</span></span>|  
|<span data-ttu-id="05daf-117">**/c\[歐\]皮 勒 :**_選項_</span><span class="sxs-lookup"><span data-stu-id="05daf-117">**/c\[ompiler\]:**_options_</span></span>|<span data-ttu-id="05daf-118">指定要傳遞至 C# 編譯器的選項。</span><span class="sxs-lookup"><span data-stu-id="05daf-118">Specifies the options to pass to the C# compiler.</span></span> <span data-ttu-id="05daf-119">所有 csc.exe 選項都受到支援，可以傳遞至編譯器。</span><span class="sxs-lookup"><span data-stu-id="05daf-119">All csc.exe options are supported as they are passed to the compiler.</span></span> <span data-ttu-id="05daf-120">這個選項可以用來指定組件必須經過簽署，並指定金鑰檔。</span><span class="sxs-lookup"><span data-stu-id="05daf-120">This can be used to specify that the assembly should be signed and to specify the key file.</span></span>|  
|<span data-ttu-id="05daf-121">**/d\[ebug\]**</span><span class="sxs-lookup"><span data-stu-id="05daf-121">**/d\[ebug\]**</span></span>|<span data-ttu-id="05daf-122">產生可以與偵錯工具搭配使用的影像。</span><span class="sxs-lookup"><span data-stu-id="05daf-122">Generates an image that can be used with a debugger.</span></span>|  
|<span data-ttu-id="05daf-123">**/f\[奧爾塞\]**</span><span class="sxs-lookup"><span data-stu-id="05daf-123">**/f\[orce\]**</span></span>|<span data-ttu-id="05daf-124">強制覆寫現有的同名組件。</span><span class="sxs-lookup"><span data-stu-id="05daf-124">Forces the overwriting of an existing assembly of the same name.</span></span> <span data-ttu-id="05daf-125">預設值為**false**。</span><span class="sxs-lookup"><span data-stu-id="05daf-125">The default is **false**.</span></span>|  
|<span data-ttu-id="05daf-126">**/help 或 /?**</span><span class="sxs-lookup"><span data-stu-id="05daf-126">**/help or /?**</span></span>|<span data-ttu-id="05daf-127">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="05daf-127">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="05daf-128">**/k\[eep\]**</span><span class="sxs-lookup"><span data-stu-id="05daf-128">**/k\[eep\]**</span></span>|<span data-ttu-id="05daf-129">將產生的原始程式檔 (Source File) 和其他暫存檔案編譯成序列化組件之後，隱藏刪除這些檔案的動作。</span><span class="sxs-lookup"><span data-stu-id="05daf-129">Suppresses the deletion of the generated source files and other temporary files after they have been compiled into the serialization assembly.</span></span> <span data-ttu-id="05daf-130">這個選項可以用來判斷工具是否正在為特定的型別產生序列化程式碼。</span><span class="sxs-lookup"><span data-stu-id="05daf-130">This can be used to determine whether the tool is generating serialization code for a particular type.</span></span>|  
|<span data-ttu-id="05daf-131">**/n\[奧洛戈\]**</span><span class="sxs-lookup"><span data-stu-id="05daf-131">**/n\[ologo\]**</span></span>|<span data-ttu-id="05daf-132">隱藏顯示 Microsoft 程式啟始資訊。</span><span class="sxs-lookup"><span data-stu-id="05daf-132">Suppresses the display of the Microsoft startup banner.</span></span>|  
|<span data-ttu-id="05daf-133">**/o\[\]ut :**_路徑_</span><span class="sxs-lookup"><span data-stu-id="05daf-133">**/o\[ut\]:**_path_</span></span>|<span data-ttu-id="05daf-134">指定要在其中儲存所產生之組件的目錄。</span><span class="sxs-lookup"><span data-stu-id="05daf-134">Specifies the directory in which to save the generated assembly.</span></span> <span data-ttu-id="05daf-135">**注意：** 產生的組件名稱是由輸入組件的名稱加上 "xmlSerializers.dll" 所組成。</span><span class="sxs-lookup"><span data-stu-id="05daf-135">**Note:**  The name of the generated assembly is composed of the name of the input assembly plus "xmlSerializers.dll".</span></span>|  
|<span data-ttu-id="05daf-136">**/p\[羅西型\]**</span><span class="sxs-lookup"><span data-stu-id="05daf-136">**/p\[roxytypes\]**</span></span>|<span data-ttu-id="05daf-137">只為 XML Web 服務 Proxy 型別產生序列化程式碼。</span><span class="sxs-lookup"><span data-stu-id="05daf-137">Generates serialization code only for the XML Web service proxy types.</span></span>|  
|<span data-ttu-id="05daf-138">**/r\[efers\]:**_程式集檔案_</span><span class="sxs-lookup"><span data-stu-id="05daf-138">**/r\[eference\]:**_assemblyfiles_</span></span>|<span data-ttu-id="05daf-139">指定要求 XML 序列化的型別所參考的組件。</span><span class="sxs-lookup"><span data-stu-id="05daf-139">Specifies the assemblies that are referenced by the types requiring XML serialization.</span></span> <span data-ttu-id="05daf-140">這個選項接受以逗號分隔多個組件檔案。</span><span class="sxs-lookup"><span data-stu-id="05daf-140">Accepts multiple assembly files separated by commas.</span></span>|  
|<span data-ttu-id="05daf-141">**/s\[ilent\]**</span><span class="sxs-lookup"><span data-stu-id="05daf-141">**/s\[ilent\]**</span></span>|<span data-ttu-id="05daf-142">隱藏顯示成功訊息。</span><span class="sxs-lookup"><span data-stu-id="05daf-142">Suppresses the display of success messages.</span></span>|  
|<span data-ttu-id="05daf-143">**/t\[\]ype :**_類型_</span><span class="sxs-lookup"><span data-stu-id="05daf-143">**/t\[ype\]:**_type_</span></span>|<span data-ttu-id="05daf-144">只為指定的型別產生序列化程式碼。</span><span class="sxs-lookup"><span data-stu-id="05daf-144">Generates serialization code only for the specified type.</span></span>|  
|<span data-ttu-id="05daf-145">**/v\[erbose\]**</span><span class="sxs-lookup"><span data-stu-id="05daf-145">**/v\[erbose\]**</span></span>|<span data-ttu-id="05daf-146">顯示詳細資訊輸出以供偵錯。</span><span class="sxs-lookup"><span data-stu-id="05daf-146">Displays verbose output for debugging.</span></span> <span data-ttu-id="05daf-147">此選項會列出無法使用 <xref:System.Xml.Serialization.XmlSerializer> 進行序列化之目標組件中的型別。</span><span class="sxs-lookup"><span data-stu-id="05daf-147">Lists types from the target assembly that cannot be serialized with the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|<span data-ttu-id="05daf-148">**/?**</span><span class="sxs-lookup"><span data-stu-id="05daf-148">**/?**</span></span>|<span data-ttu-id="05daf-149">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="05daf-149">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05daf-150">備註</span><span class="sxs-lookup"><span data-stu-id="05daf-150">Remarks</span></span>  
 <span data-ttu-id="05daf-151">如果未使用 XML 序列化程式產生器，則每當應用程式執行時，<xref:System.Xml.Serialization.XmlSerializer> 便會為每個型別產生序列化程式碼和序列化組件。</span><span class="sxs-lookup"><span data-stu-id="05daf-151">When the XML Serializer Generator is not used, a <xref:System.Xml.Serialization.XmlSerializer> generates serialization code and a serialization assembly for each type every time an application is run.</span></span> <span data-ttu-id="05daf-152">為了提高 XML 序列化啟動的性能,請使用 Sgen.exe 工具提前生成這些程式集。</span><span class="sxs-lookup"><span data-stu-id="05daf-152">To improve the performance of XML serialization startup, use the Sgen.exe tool to generate those assemblies in advance.</span></span> <span data-ttu-id="05daf-153">然後，這些組件便可以與應用程式一起部署。</span><span class="sxs-lookup"><span data-stu-id="05daf-153">These assemblies can then be deployed with the application.</span></span>  
  
 <span data-ttu-id="05daf-154">XML 序列化程式產生器也可以改善用戶端使用 XML Web Service Proxy 與伺服器進行通訊的效能，因為在第一次載入型別時，序列化處理序並不會影響到效能。</span><span class="sxs-lookup"><span data-stu-id="05daf-154">The XML Serializer Generator can also improve the performance of clients that use XML Web service proxies to communicate with servers because the serialization process will not incur a performance hit when the type is loaded the first time.</span></span>  
  
 <span data-ttu-id="05daf-155">這些產生的組件無法在 Web 服務的伺服器端上使用。</span><span class="sxs-lookup"><span data-stu-id="05daf-155">These generated assemblies cannot be used on the server side of a Web service.</span></span> <span data-ttu-id="05daf-156">這個工具只能在 Web 服務用戶端和手動序列化案例中使用。</span><span class="sxs-lookup"><span data-stu-id="05daf-156">This tool is only for Web service clients and manual serialization scenarios.</span></span>  
  
 <span data-ttu-id="05daf-157">如果含有要序列化之型別的組件名稱為 MyType.dll，關聯的序列化組件名稱就會是 MyType.XmlSerializers.dll。</span><span class="sxs-lookup"><span data-stu-id="05daf-157">If the assembly containing the type to serialize is named MyType.dll, then the associated serialization assembly will be named MyType.XmlSerializers.dll.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="05daf-158">範例</span><span class="sxs-lookup"><span data-stu-id="05daf-158">Examples</span></span>  
 <span data-ttu-id="05daf-159">下列命令會建立名為 Data.XmlSerializers.dll 的組件，用以序列化 Data.dll 組件中所包含的所有型別。</span><span class="sxs-lookup"><span data-stu-id="05daf-159">The following command creates an assembly named Data.XmlSerializers.dll for serializing all the types contained in the assembly named Data.dll.</span></span>  
  
```console  
sgen Data.dll
```  
  
 <span data-ttu-id="05daf-160">Data.XmlSerializers.dll 組件可以從程式碼參考，而該程式碼必須序列化及還原序列化 Data.dll 中的型別。</span><span class="sxs-lookup"><span data-stu-id="05daf-160">The Data.XmlSerializers.dll assembly can be referenced from code that needs to serialize and deserialize the types in Data.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05daf-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05daf-161">See also</span></span>

- [<span data-ttu-id="05daf-162">工具</span><span class="sxs-lookup"><span data-stu-id="05daf-162">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="05daf-163">指令提示</span><span class="sxs-lookup"><span data-stu-id="05daf-163">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
