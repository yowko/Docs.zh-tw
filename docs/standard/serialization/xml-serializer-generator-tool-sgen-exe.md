---
title: XML 序列化程式產生器工具 (Sgen.exe)
ms.date: 03/30/2017
ms.assetid: cc1d1f1c-fb26-4be9-885a-3fe84c81cec6
ms.openlocfilehash: 54afa99af3365c3be8a9662905467fbcaf4e8aa3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589175"
---
# <a name="xml-serializer-generator-tool-sgenexe"></a><span data-ttu-id="8ff6f-102">XML 序列化程式產生器工具 (Sgen.exe)</span><span class="sxs-lookup"><span data-stu-id="8ff6f-102">XML Serializer Generator Tool (Sgen.exe)</span></span>
<span data-ttu-id="8ff6f-103">XML 序列化程式產生器會為指定組件中的型別建立 XML 序列化 (Serialization) 組件，以改善 <xref:System.Xml.Serialization.XmlSerializer> 在序列化或還原序列化指定型別物件時的啟動效能。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-103">The XML Serializer Generator creates an XML serialization assembly for types in a specified assembly in order to improve the startup performance of a <xref:System.Xml.Serialization.XmlSerializer> when it serializes or deserializes objects of the specified types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ff6f-104">語法</span><span class="sxs-lookup"><span data-stu-id="8ff6f-104">Syntax</span></span>  
  
```  
sgen [options]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8ff6f-105">參數</span><span class="sxs-lookup"><span data-stu-id="8ff6f-105">Parameters</span></span>  
  
|<span data-ttu-id="8ff6f-106">選項</span><span class="sxs-lookup"><span data-stu-id="8ff6f-106">Option</span></span>|<span data-ttu-id="8ff6f-107">描述</span><span class="sxs-lookup"><span data-stu-id="8ff6f-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="8ff6f-108">**/a**[**ssembly**]**:***filename*</span><span class="sxs-lookup"><span data-stu-id="8ff6f-108">**/a**[**ssembly**]**:***filename*</span></span>|<span data-ttu-id="8ff6f-109">為組件中包含的所有類型或 *filename* 所指定的可執行檔產生序列化程式碼。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-109">Generates serialization code for all the types contained in the assembly or executable specified by *filename*.</span></span> <span data-ttu-id="8ff6f-110">只能提供一個檔名。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-110">Only one file name can be provided.</span></span> <span data-ttu-id="8ff6f-111">如果重複使用這個引數，則會使用最後一個檔名。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-111">If this argument is repeated, the last file name is used.</span></span>|  
|<span data-ttu-id="8ff6f-112">**/c[ompiler]:** *options*</span><span class="sxs-lookup"><span data-stu-id="8ff6f-112">**/c[ompiler]:** *options*</span></span>|<span data-ttu-id="8ff6f-113">指定要傳遞至 C# 編譯器的選項。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-113">Specifies the options to pass to the C# compiler.</span></span> <span data-ttu-id="8ff6f-114">所有 csc.exe 選項都受到支援，可以傳遞至編譯器。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-114">All csc.exe options are supported as they are passed to the compiler.</span></span> <span data-ttu-id="8ff6f-115">這個選項可以用來指定組件必須經過簽署，並指定金鑰檔。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-115">This can be used to specify that the assembly should be signed and to specify the key file.</span></span>|  
|<span data-ttu-id="8ff6f-116">**/d**[**ebug**]</span><span class="sxs-lookup"><span data-stu-id="8ff6f-116">**/d**[**ebug**]</span></span>|<span data-ttu-id="8ff6f-117">產生可以與偵錯工具搭配使用的影像。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-117">Generates an image that can be used with a debugger.</span></span>|  
|<span data-ttu-id="8ff6f-118">**/f[orce]**</span><span class="sxs-lookup"><span data-stu-id="8ff6f-118">**/f[orce]**</span></span>|<span data-ttu-id="8ff6f-119">強制覆寫現有的同名組件。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-119">Forces the overwriting of an existing assembly of the same name.</span></span> <span data-ttu-id="8ff6f-120">預設值為 **false**。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-120">The default is **false**.</span></span>|  
|<span data-ttu-id="8ff6f-121">**/help 或 /?**</span><span class="sxs-lookup"><span data-stu-id="8ff6f-121">**/help or /?**</span></span>|<span data-ttu-id="8ff6f-122">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-122">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="8ff6f-123">**/k**[**eep**]</span><span class="sxs-lookup"><span data-stu-id="8ff6f-123">**/k**[**eep**]</span></span>|<span data-ttu-id="8ff6f-124">將產生的原始程式檔 (Source File) 和其他暫存檔案編譯成序列化組件之後，隱藏刪除這些檔案的動作。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-124">Suppresses the deletion of the generated source files and other temporary files after they have been compiled into the serialization assembly.</span></span> <span data-ttu-id="8ff6f-125">這個選項可以用來判斷工具是否正在為特定的型別產生序列化程式碼。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-125">This can be used to determine whether the tool is generating serialization code for a particular type.</span></span>|  
|<span data-ttu-id="8ff6f-126">**/n**[**ologo**]</span><span class="sxs-lookup"><span data-stu-id="8ff6f-126">**/n**[**ologo**]</span></span>|<span data-ttu-id="8ff6f-127">隱藏顯示 Microsoft 程式啟始資訊。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-127">Suppresses the display of the Microsoft startup banner.</span></span>|  
|<span data-ttu-id="8ff6f-128">**/o**[**ut**] **: * * * 路徑*</span><span class="sxs-lookup"><span data-stu-id="8ff6f-128">**/o**[**ut**]**:***path*</span></span>|<span data-ttu-id="8ff6f-129">指定要在其中儲存所產生之組件的目錄。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-129">Specifies the directory in which to save the generated assembly.</span></span> <span data-ttu-id="8ff6f-130">**注意：** 產生的組件名稱是由輸入組件的名稱加上 "xmlSerializers.dll" 所組成。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-130">**Note:**  The name of the generated assembly is composed of the name of the input assembly plus "xmlSerializers.dll".</span></span>|  
|<span data-ttu-id="8ff6f-131">**/p**[**roxytypes**]</span><span class="sxs-lookup"><span data-stu-id="8ff6f-131">**/p**[**roxytypes**]</span></span>|<span data-ttu-id="8ff6f-132">只為 XML Web 服務 Proxy 型別產生序列化程式碼。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-132">Generates serialization code only for the XML Web service proxy types.</span></span>|  
|<span data-ttu-id="8ff6f-133">**/r**[**eference**]**:***assemblyfiles*</span><span class="sxs-lookup"><span data-stu-id="8ff6f-133">**/r**[**eference**]**:***assemblyfiles*</span></span>|<span data-ttu-id="8ff6f-134">指定要求 XML 序列化的型別所參考的組件。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-134">Specifies the assemblies that are referenced by the types requiring XML serialization.</span></span> <span data-ttu-id="8ff6f-135">這個選項接受以逗號分隔多個組件檔案。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-135">Accepts multiple assembly files separated by commas.</span></span>|  
|<span data-ttu-id="8ff6f-136">**/s**[**ilent**]</span><span class="sxs-lookup"><span data-stu-id="8ff6f-136">**/s**[**ilent**]</span></span>|<span data-ttu-id="8ff6f-137">隱藏顯示成功訊息。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-137">Suppresses the display of success messages.</span></span>|  
|<span data-ttu-id="8ff6f-138">**/t**[**ype**]**:***type*</span><span class="sxs-lookup"><span data-stu-id="8ff6f-138">**/t**[**ype**]**:***type*</span></span>|<span data-ttu-id="8ff6f-139">只為指定的型別產生序列化程式碼。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-139">Generates serialization code only for the specified type.</span></span>|  
|<span data-ttu-id="8ff6f-140">**/v**[**erbose**]</span><span class="sxs-lookup"><span data-stu-id="8ff6f-140">**/v**[**erbose**]</span></span>|<span data-ttu-id="8ff6f-141">顯示詳細資訊輸出以供偵錯。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-141">Displays verbose output for debugging.</span></span> <span data-ttu-id="8ff6f-142">此選項會列出無法使用 <xref:System.Xml.Serialization.XmlSerializer> 進行序列化之目標組件中的型別。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-142">Lists types from the target assembly that cannot be serialized with the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
|<span data-ttu-id="8ff6f-143">**/?**</span><span class="sxs-lookup"><span data-stu-id="8ff6f-143">**/?**</span></span>|<span data-ttu-id="8ff6f-144">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-144">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ff6f-145">備註</span><span class="sxs-lookup"><span data-stu-id="8ff6f-145">Remarks</span></span>  
 <span data-ttu-id="8ff6f-146">如果未使用 XML 序列化程式產生器，則每當應用程式執行時，<xref:System.Xml.Serialization.XmlSerializer> 便會為每個型別產生序列化程式碼和序列化組件。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-146">When the XML Serializer Generator is not used, a <xref:System.Xml.Serialization.XmlSerializer> generates serialization code and a serialization assembly for each type every time an application is run.</span></span> <span data-ttu-id="8ff6f-147">若要改善效能的 XML 序列化啟動，使用 Sgen.exe 工具事先產生這些組件。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-147">To improve the performance of XML serialization startup, use the Sgen.exe tool to generate those assemblies in advance.</span></span> <span data-ttu-id="8ff6f-148">然後，這些組件便可以與應用程式一起部署。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-148">These assemblies can then be deployed with the application.</span></span>  
  
 <span data-ttu-id="8ff6f-149">XML 序列化程式產生器也可以改善用戶端使用 XML Web Service Proxy 與伺服器進行通訊的效能，因為在第一次載入型別時，序列化處理序並不會影響到效能。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-149">The XML Serializer Generator can also improve the performance of clients that use XML Web service proxies to communicate with servers because the serialization process will not incur a performance hit when the type is loaded the first time.</span></span>  
  
 <span data-ttu-id="8ff6f-150">這些產生的組件無法在 Web 服務的伺服器端上使用。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-150">These generated assemblies cannot be used on the server side of a Web service.</span></span> <span data-ttu-id="8ff6f-151">這個工具只能在 Web 服務用戶端和手動序列化案例中使用。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-151">This tool is only for Web service clients and manual serialization scenarios.</span></span>  
  
 <span data-ttu-id="8ff6f-152">如果含有要序列化之型別的組件名稱為 MyType.dll，關聯的序列化組件名稱就會是 MyType.XmlSerializers.dll。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-152">If the assembly containing the type to serialize is named MyType.dll, then the associated serialization assembly will be named MyType.XmlSerializers.dll.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="8ff6f-153">範例</span><span class="sxs-lookup"><span data-stu-id="8ff6f-153">Examples</span></span>  
 <span data-ttu-id="8ff6f-154">下列命令會建立名為 Data.XmlSerializers.dll 的組件，用以序列化 Data.dll 組件中所包含的所有型別。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-154">The following command creates an assembly named Data.XmlSerializers.dll for serializing all the types contained in the assembly named Data.dll.</span></span>  
  
```  
sgen Data.dll   
```  
  
 <span data-ttu-id="8ff6f-155">Data.XmlSerializers.dll 組件可以從程式碼參考，而該程式碼必須序列化及還原序列化 Data.dll 中的型別。</span><span class="sxs-lookup"><span data-stu-id="8ff6f-155">The Data.XmlSerializers.dll assembly can be referenced from code that needs to serialize and deserialize the types in Data.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ff6f-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ff6f-156">See Also</span></span>  
 [<span data-ttu-id="8ff6f-157">工具</span><span class="sxs-lookup"><span data-stu-id="8ff6f-157">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="8ff6f-158">XML Web Service 概觀</span><span class="sxs-lookup"><span data-stu-id="8ff6f-158">XML Web Services Overview</span></span>](https://msdn.microsoft.com/library/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d)  
 [<span data-ttu-id="8ff6f-159">命令提示字元</span><span class="sxs-lookup"><span data-stu-id="8ff6f-159">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
