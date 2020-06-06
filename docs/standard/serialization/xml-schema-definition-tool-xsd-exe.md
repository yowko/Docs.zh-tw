---
title: XML Schema Definition Tool (Xsd.exe)
description: XML 序列化程式產生器會針對指定元件中的類型建立 XML 序列化元件，以改善 XmlSerializer 的啟動效能。
ms.date: 03/30/2017
ms.assetid: a6e6e65c-347f-4494-9457-653bf29baac2
ms.openlocfilehash: 0275ecfebd427feb104013024654d4a0bc98748a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "84288975"
---
# <a name="xml-schema-definition-tool-xsdexe"></a><span data-ttu-id="b6f52-103">XML Schema Definition Tool (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="b6f52-103">XML Schema Definition Tool (Xsd.exe)</span></span>

<span data-ttu-id="b6f52-104">XML 結構描述定義工具 (Xsd.exe) 可以從 XDR、XML 和 XSD 檔案或從執行階段組件的類別中，產生 XML 結構描述或 Common Language Runtime 類別。</span><span class="sxs-lookup"><span data-stu-id="b6f52-104">The XML Schema Definition (Xsd.exe) tool generates XML schema or common language runtime classes from XDR, XML, and XSD files, or from classes in a runtime assembly.</span></span>

<span data-ttu-id="b6f52-105">XML 架構定義工具（Xsd.exe）通常可以在下列路徑中找到： </span><span class="sxs-lookup"><span data-stu-id="b6f52-105">The XML Schema Definition tool (Xsd.exe) usually can be found in the following path:</span></span>\
<span data-ttu-id="b6f52-106">_C： \\ Program Files （x86） \\ Microsoft sdk \\ Windows \\ {version} \\ Bin \\ NETFX {version} 工具\\_</span><span class="sxs-lookup"><span data-stu-id="b6f52-106">_C:\\Program Files (x86)\\Microsoft SDKs\\Windows\\{version}\\bin\\NETFX {version} Tools\\_</span></span>

## <a name="syntax"></a><span data-ttu-id="b6f52-107">語法</span><span class="sxs-lookup"><span data-stu-id="b6f52-107">Syntax</span></span>

<span data-ttu-id="b6f52-108">從命令列執行工具。</span><span class="sxs-lookup"><span data-stu-id="b6f52-108">Run the tool from the command line.</span></span>

```console
xsd file.xdr [-outputdir:directory][/parameters:file.xml]
xsd file.xml [-outputdir:directory] [/parameters:file.xml]
xsd file.xsd {/classes | /dataset} [/element:element]
             [/enableLinqDataSet] [/language:language]
                          [/namespace:namespace] [-outputdir:directory] [URI:uri]
                          [/parameters:file.xml]
xsd {file.dll | file.exe} [-outputdir:directory] [/type:typename [...]][/parameters:file.xml]
```
  
> [!TIP]
> <span data-ttu-id="b6f52-109">若要讓 .NET Framework 工具正常運作，您必須 `Path` `Include` 正確地設定、和 `Lib` 環境變數。</span><span class="sxs-lookup"><span data-stu-id="b6f52-109">For .NET Framework tools to function properly, you must set your `Path`, `Include`, and `Lib` environment variables correctly.</span></span> <span data-ttu-id="b6f52-110">藉由執行 SDKVars （位於 \V2.0\Bin 目錄中）來設定這些環境變數 \<SDK> 。</span><span class="sxs-lookup"><span data-stu-id="b6f52-110">Set these environment variables by running SDKVars.bat, which is located in the \<SDK>\v2.0\Bin directory.</span></span> <span data-ttu-id="b6f52-111">SDKVars.bat 必須在每一個命令提示字元中執行。</span><span class="sxs-lookup"><span data-stu-id="b6f52-111">SDKVars.bat must be executed in every command shell.</span></span>

## <a name="argument"></a><span data-ttu-id="b6f52-112">引數</span><span class="sxs-lookup"><span data-stu-id="b6f52-112">Argument</span></span>

|<span data-ttu-id="b6f52-113">引數</span><span class="sxs-lookup"><span data-stu-id="b6f52-113">Argument</span></span>|<span data-ttu-id="b6f52-114">描述</span><span class="sxs-lookup"><span data-stu-id="b6f52-114">Description</span></span>|
|--------------|-----------------|
|<span data-ttu-id="b6f52-115">*副檔名*</span><span class="sxs-lookup"><span data-stu-id="b6f52-115">*file.extension*</span></span>|<span data-ttu-id="b6f52-116">指定要轉換的輸入檔。</span><span class="sxs-lookup"><span data-stu-id="b6f52-116">Specifies the input file to convert.</span></span> <span data-ttu-id="b6f52-117">您必須將此延伸模組指定為下列其中一項： xdr、.xml、.xsd、.dll 或 .exe。</span><span class="sxs-lookup"><span data-stu-id="b6f52-117">You must specify the extension as one of the following: .xdr, .xml, .xsd, .dll, or .exe.</span></span><br /><br /> <span data-ttu-id="b6f52-118">如果指定 XDR 結構描述檔 (副檔名為 .xdr )，Xsd.exe 會將 XDR 結構描述轉換成 XSD 結構描述。</span><span class="sxs-lookup"><span data-stu-id="b6f52-118">If you specify an XDR schema file (.xdr extension), Xsd.exe converts the XDR schema to an XSD schema.</span></span> <span data-ttu-id="b6f52-119">輸出檔有和 XDR 結構描述一樣的名稱，但是具有 .xsd 副檔名。</span><span class="sxs-lookup"><span data-stu-id="b6f52-119">The output file has the same name as the XDR schema, but with the .xsd extension.</span></span><br /><br /> <span data-ttu-id="b6f52-120">如果指定 XML 檔 (副檔名為 .xml )，Xsd.exe 會從檔案中的資料推斷結構描述，然後產生 XSD 結構描述。</span><span class="sxs-lookup"><span data-stu-id="b6f52-120">If you specify an XML file (.xml extension), Xsd.exe infers a schema from the data in the file and produces an XSD schema.</span></span> <span data-ttu-id="b6f52-121">輸出檔有和 XML 檔一樣的名稱，但是具有 .xsd 副檔名。</span><span class="sxs-lookup"><span data-stu-id="b6f52-121">The output file has the same name as the XML file, but with the .xsd extension.</span></span><br /><br /> <span data-ttu-id="b6f52-122">如果指定 XML 結構描述檔 (.xsd 副檔名)，Xsd.exe 會產生對應到 XML 結構描述之 Runtime 物件的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="b6f52-122">If you specify an XML schema file (.xsd extension), Xsd.exe generates source code for runtime objects that correspond to the XML schema.</span></span><br /><br /> <span data-ttu-id="b6f52-123">如果指定執行階段組件檔 (.exe 或 .dll 副檔名)，Xsd.exe 會產生該組件中一個或多個型別的結構描述。</span><span class="sxs-lookup"><span data-stu-id="b6f52-123">If you specify a runtime assembly file (.exe or .dll extension), Xsd.exe generates schemas for one or more types in that assembly.</span></span> <span data-ttu-id="b6f52-124">您可以使用 `/type` 選項來指定要產生結構描述的型別。</span><span class="sxs-lookup"><span data-stu-id="b6f52-124">You can use the `/type` option to specify the types for which to generate schemas.</span></span> <span data-ttu-id="b6f52-125">輸出結構描述被命名為 schema0.xsd、schema1.xsd 等等。</span><span class="sxs-lookup"><span data-stu-id="b6f52-125">The output schemas are named schema0.xsd, schema1.xsd, and so on.</span></span> <span data-ttu-id="b6f52-126">只有在指定的型別使用 `XMLRoot` 自訂屬性來指定命名空間 (Namespace) 時，Xsd.exe 才能產生多個結構描述。</span><span class="sxs-lookup"><span data-stu-id="b6f52-126">Xsd.exe produces multiple schemas only if the given types specify a namespace using the `XMLRoot` custom attribute.</span></span>|

## <a name="general-options"></a><span data-ttu-id="b6f52-127">一般選項</span><span class="sxs-lookup"><span data-stu-id="b6f52-127">General Options</span></span>

|<span data-ttu-id="b6f52-128">選項</span><span class="sxs-lookup"><span data-stu-id="b6f52-128">Option</span></span>|<span data-ttu-id="b6f52-129">描述</span><span class="sxs-lookup"><span data-stu-id="b6f52-129">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="b6f52-130">**/h \[ elp\]**</span><span class="sxs-lookup"><span data-stu-id="b6f52-130">**/h\[elp\]**</span></span>|<span data-ttu-id="b6f52-131">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="b6f52-131">Displays command syntax and options for the tool.</span></span>|
|<span data-ttu-id="b6f52-132">**/o \[ utputdir \] ：**_directory_</span><span class="sxs-lookup"><span data-stu-id="b6f52-132">**/o\[utputdir\]:**_directory_</span></span>|<span data-ttu-id="b6f52-133">指定輸出檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="b6f52-133">Specifies the directory for output files.</span></span> <span data-ttu-id="b6f52-134">這個引數只可以使用一次。</span><span class="sxs-lookup"><span data-stu-id="b6f52-134">This argument can appear only once.</span></span> <span data-ttu-id="b6f52-135">預設值是目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="b6f52-135">The default is the current directory.</span></span>|
|<span data-ttu-id="b6f52-136">**/?**</span><span class="sxs-lookup"><span data-stu-id="b6f52-136">**/?**</span></span>|<span data-ttu-id="b6f52-137">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="b6f52-137">Displays command syntax and options for the tool.</span></span>|
|<span data-ttu-id="b6f52-138">**/p \[ arameters \] ：**_file .xml_</span><span class="sxs-lookup"><span data-stu-id="b6f52-138">**/p\[arameters\]:**_file.xml_</span></span>|<span data-ttu-id="b6f52-139">從指定的 .xml 檔案，讀取各種作業模式的選項。</span><span class="sxs-lookup"><span data-stu-id="b6f52-139">Read options for various operation modes from the specified .xml file.</span></span> <span data-ttu-id="b6f52-140">簡短形式為 `/p:`。</span><span class="sxs-lookup"><span data-stu-id="b6f52-140">The short form is `/p:`.</span></span> <span data-ttu-id="b6f52-141">如需詳細資訊，請參閱[備註](#remarks)一節。</span><span class="sxs-lookup"><span data-stu-id="b6f52-141">For more information, see the [Remarks](#remarks) section.</span></span>|

## <a name="xsd-file-options"></a><span data-ttu-id="b6f52-142">XSD 檔案選項</span><span class="sxs-lookup"><span data-stu-id="b6f52-142">XSD File Options</span></span>
 <span data-ttu-id="b6f52-143">您只能為 .xsd 檔指定下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="b6f52-143">You must specify only one of the following options for .xsd files.</span></span>

|<span data-ttu-id="b6f52-144">選項</span><span class="sxs-lookup"><span data-stu-id="b6f52-144">Option</span></span>|<span data-ttu-id="b6f52-145">描述</span><span class="sxs-lookup"><span data-stu-id="b6f52-145">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="b6f52-146">**/c \[ lasses\]**</span><span class="sxs-lookup"><span data-stu-id="b6f52-146">**/c\[lasses\]**</span></span>|<span data-ttu-id="b6f52-147">產生對應到指定的結構描述的類別。</span><span class="sxs-lookup"><span data-stu-id="b6f52-147">Generates classes that correspond to the specified schema.</span></span> <span data-ttu-id="b6f52-148">若要將 XML 資料讀入物件，請使用 <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="b6f52-148">To read XML data into the object, use the <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>|
|<span data-ttu-id="b6f52-149">**/d \[ ataset\]**</span><span class="sxs-lookup"><span data-stu-id="b6f52-149">**/d\[ataset\]**</span></span>|<span data-ttu-id="b6f52-150">產生衍生自 <xref:System.Data.DataSet> 的類別，對應到指定的結構描述。</span><span class="sxs-lookup"><span data-stu-id="b6f52-150">Generates a class derived from <xref:System.Data.DataSet> that corresponds to the specified schema.</span></span> <span data-ttu-id="b6f52-151">若要將 XML 資料讀入衍生類別，請使用 <xref:System.Data.DataSet.ReadXml%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="b6f52-151">To read XML data into the derived class, use the <xref:System.Data.DataSet.ReadXml%2A?displayProperty=nameWithType> method.</span></span>|

 <span data-ttu-id="b6f52-152">您也可以為 .xsd 檔指定下列任何選項：</span><span class="sxs-lookup"><span data-stu-id="b6f52-152">You can also specify any of the following options for .xsd files.</span></span>

|<span data-ttu-id="b6f52-153">選項</span><span class="sxs-lookup"><span data-stu-id="b6f52-153">Option</span></span>|<span data-ttu-id="b6f52-154">描述</span><span class="sxs-lookup"><span data-stu-id="b6f52-154">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="b6f52-155">**/e \[ lement \] ：**_元素_</span><span class="sxs-lookup"><span data-stu-id="b6f52-155">**/e\[lement\]:**_element_</span></span>|<span data-ttu-id="b6f52-156">指定所要產生程式碼的結構描述中的項目。</span><span class="sxs-lookup"><span data-stu-id="b6f52-156">Specifies the element in the schema to generate code for.</span></span> <span data-ttu-id="b6f52-157">根據預設，會輸入所有項目。</span><span class="sxs-lookup"><span data-stu-id="b6f52-157">By default all elements are typed.</span></span> <span data-ttu-id="b6f52-158">您可以多次指定這個引數。</span><span class="sxs-lookup"><span data-stu-id="b6f52-158">You can specify this argument more than once.</span></span>|
|<span data-ttu-id="b6f52-159">**/enableDataBinding**</span><span class="sxs-lookup"><span data-stu-id="b6f52-159">**/enableDataBinding**</span></span>|<span data-ttu-id="b6f52-160">在所有產生的型別上實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面，以啟用資料繫結 (Data Binding)。</span><span class="sxs-lookup"><span data-stu-id="b6f52-160">Implements the <xref:System.ComponentModel.INotifyPropertyChanged> interface on all generated types to enable data binding.</span></span> <span data-ttu-id="b6f52-161">簡短形式為 `/edb`。</span><span class="sxs-lookup"><span data-stu-id="b6f52-161">The short form is `/edb`.</span></span>|
|<span data-ttu-id="b6f52-162">**/enableLinqDataSet**</span><span class="sxs-lookup"><span data-stu-id="b6f52-162">**/enableLinqDataSet**</span></span>|<span data-ttu-id="b6f52-163">（簡短形式： `/eld` .）指定所產生的資料集可以使用 LINQ to DataSet 來查詢。</span><span class="sxs-lookup"><span data-stu-id="b6f52-163">(Short form: `/eld`.) Specifies that the generated DataSet can be queried against using LINQ to DataSet.</span></span> <span data-ttu-id="b6f52-164">如果也指定了 /dataset 選項，就會使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="b6f52-164">This option is used when the /dataset option is also specified.</span></span> <span data-ttu-id="b6f52-165">如需詳細資訊，請參閱 [LINQ to DataSet 概觀](../../framework/data/adonet/linq-to-dataset-overview.md)和[查詢具類型資料集](../../framework/data/adonet/querying-typed-datasets.md)。</span><span class="sxs-lookup"><span data-stu-id="b6f52-165">For more information, see [LINQ to DataSet Overview](../../framework/data/adonet/linq-to-dataset-overview.md) and [Querying Typed DataSets](../../framework/data/adonet/querying-typed-datasets.md).</span></span> <span data-ttu-id="b6f52-166">如需使用 LINQ 的一般資訊，請參閱[語言整合式查詢（linq）-c #](../../csharp/programming-guide/concepts/linq/index.md)或[語言整合查詢（linq）-Visual Basic](../../visual-basic/programming-guide/concepts/linq/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b6f52-166">For general information about using LINQ, see [Language-Integrated Query (LINQ) - C#](../../csharp/programming-guide/concepts/linq/index.md) or [Language-Integrated Query (LINQ) - Visual Basic](../../visual-basic/programming-guide/concepts/linq/index.md).</span></span>|
|<span data-ttu-id="b6f52-167">**/f \[ ields\]**</span><span class="sxs-lookup"><span data-stu-id="b6f52-167">**/f\[ields\]**</span></span>|<span data-ttu-id="b6f52-168">產生欄位，而不是產生屬性。</span><span class="sxs-lookup"><span data-stu-id="b6f52-168">Generates fields instead of properties.</span></span> <span data-ttu-id="b6f52-169">根據預設，會產生屬性。</span><span class="sxs-lookup"><span data-stu-id="b6f52-169">By default, properties are generated.</span></span>|
|<span data-ttu-id="b6f52-170">**/l \[ anguage \] ：**_language_</span><span class="sxs-lookup"><span data-stu-id="b6f52-170">**/l\[anguage\]:**_language_</span></span>|<span data-ttu-id="b6f52-171">指定要使用的程式語言。</span><span class="sxs-lookup"><span data-stu-id="b6f52-171">Specifies the programming language to use.</span></span> <span data-ttu-id="b6f52-172">可以選擇 `CS` (C#，此為預設值)、`VB` (Visual Basic)、`JS` (JScript) 或 `VJS` (Visual J#)。</span><span class="sxs-lookup"><span data-stu-id="b6f52-172">Choose from `CS` (C#, which is the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="b6f52-173">您也可以對實作 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> 的類別指定完整名稱。</span><span class="sxs-lookup"><span data-stu-id="b6f52-173">You can also specify a fully qualified name for a class implementing <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType></span></span>|
|<span data-ttu-id="b6f52-174">**/n \[ amespace \] ：**_命名空間_</span><span class="sxs-lookup"><span data-stu-id="b6f52-174">**/n\[amespace\]:**_namespace_</span></span>|<span data-ttu-id="b6f52-175">指定產生的型別的執行階段命名空間。</span><span class="sxs-lookup"><span data-stu-id="b6f52-175">Specifies the runtime namespace for the generated types.</span></span> <span data-ttu-id="b6f52-176">預設命名空間是 `Schemas`。</span><span class="sxs-lookup"><span data-stu-id="b6f52-176">The default namespace is `Schemas`.</span></span>|
|<span data-ttu-id="b6f52-177">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="b6f52-177">**/nologo**</span></span>|<span data-ttu-id="b6f52-178">隱藏產品啟始畫面。</span><span class="sxs-lookup"><span data-stu-id="b6f52-178">Suppresses the banner.</span></span>|
|<span data-ttu-id="b6f52-179">**/order**</span><span class="sxs-lookup"><span data-stu-id="b6f52-179">**/order**</span></span>|<span data-ttu-id="b6f52-180">在所有物件成員上產生明確順序識別項。</span><span class="sxs-lookup"><span data-stu-id="b6f52-180">Generates explicit order identifiers on all particle members.</span></span>|
|<span data-ttu-id="b6f52-181">**/o \[ \] 內容：**_directoryName_</span><span class="sxs-lookup"><span data-stu-id="b6f52-181">**/o\[ut\]:**_directoryName_</span></span>|<span data-ttu-id="b6f52-182">指定要在其中放置檔案的輸出目錄。</span><span class="sxs-lookup"><span data-stu-id="b6f52-182">Specifies the output directory to place the files in.</span></span> <span data-ttu-id="b6f52-183">預設值是目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="b6f52-183">The default is the current directory.</span></span>|
|<span data-ttu-id="b6f52-184">**/u \[ ri \] ：**_uri_</span><span class="sxs-lookup"><span data-stu-id="b6f52-184">**/u\[ri\]:**_uri_</span></span>|<span data-ttu-id="b6f52-185">指定所要產生程式碼的結構描述中項目的 URI。</span><span class="sxs-lookup"><span data-stu-id="b6f52-185">Specifies the URI for the elements in the schema to generate code for.</span></span> <span data-ttu-id="b6f52-186">這個 URI 如果存在，會套用到所有以 `/element` 選項指定的項目。</span><span class="sxs-lookup"><span data-stu-id="b6f52-186">This URI, if present, applies to all elements specified with the `/element` option.</span></span>|

## <a name="dll-and-exe-file-options"></a><span data-ttu-id="b6f52-187">DLL 和 EXE 檔案選項</span><span class="sxs-lookup"><span data-stu-id="b6f52-187">DLL and EXE File Options</span></span>

|<span data-ttu-id="b6f52-188">選項</span><span class="sxs-lookup"><span data-stu-id="b6f52-188">Option</span></span>|<span data-ttu-id="b6f52-189">描述</span><span class="sxs-lookup"><span data-stu-id="b6f52-189">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="b6f52-190">/t_類型名稱_ \*\* \[ \] ：\*\* typename</span><span class="sxs-lookup"><span data-stu-id="b6f52-190">**/t\[ype\]:**_typename_</span></span>|<span data-ttu-id="b6f52-191">指定所要建立結構描述的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="b6f52-191">Specifies the name of the type to create a schema for.</span></span> <span data-ttu-id="b6f52-192">您可以指定多個型別引數。</span><span class="sxs-lookup"><span data-stu-id="b6f52-192">You can specify multiple type arguments.</span></span> <span data-ttu-id="b6f52-193">如果 *typename* 沒有指定命名空間，Xsd.exe 會以指定的類型比對組件中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="b6f52-193">If *typename* does not specify a namespace, Xsd.exe matches all types in the assembly with the specified type.</span></span> <span data-ttu-id="b6f52-194">如果 *typename* 指定命名空間，只有該類型會被比對。</span><span class="sxs-lookup"><span data-stu-id="b6f52-194">If *typename* specifies a namespace, only that type is matched.</span></span> <span data-ttu-id="b6f52-195">如果 *typename* 結尾為星號字元 (\*)，則工具會比對 \* 之前以這個字串為開頭的所有類型。</span><span class="sxs-lookup"><span data-stu-id="b6f52-195">If *typename* ends with an asterisk character (\*), the tool matches all types that start with the string preceding the \*.</span></span> <span data-ttu-id="b6f52-196">如果省略 `/type` 選項，Xsd.exe 會產生組件中所有型別的結構描述。</span><span class="sxs-lookup"><span data-stu-id="b6f52-196">If you omit the `/type` option, Xsd.exe generates schemas for all types in the assembly.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b6f52-197">備註</span><span class="sxs-lookup"><span data-stu-id="b6f52-197">Remarks</span></span>

<span data-ttu-id="b6f52-198">下表列出 Xsd.exe 執行的作業。</span><span class="sxs-lookup"><span data-stu-id="b6f52-198">The following table shows the operations that Xsd.exe performs.</span></span>

| | |
|------------|-----------------|
|<span data-ttu-id="b6f52-199">XDR 轉換成 XSD</span><span class="sxs-lookup"><span data-stu-id="b6f52-199">XDR to XSD</span></span>|<span data-ttu-id="b6f52-200">從 XML-Data-Reduced 結構描述檔中產生 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="b6f52-200">Generates an XML schema from an XML-Data-Reduced schema file.</span></span> <span data-ttu-id="b6f52-201">XDR 是早期 XML 架構的結構描述。</span><span class="sxs-lookup"><span data-stu-id="b6f52-201">XDR is an early XML-based schema format.</span></span>|
|<span data-ttu-id="b6f52-202">XML 轉換成 XSD</span><span class="sxs-lookup"><span data-stu-id="b6f52-202">XML to XSD</span></span>|<span data-ttu-id="b6f52-203">從 XML 檔案中產生 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="b6f52-203">Generates an XML schema from an XML file.</span></span>|
|<span data-ttu-id="b6f52-204">XSD 轉換成 DataSet</span><span class="sxs-lookup"><span data-stu-id="b6f52-204">XSD to DataSet</span></span>|<span data-ttu-id="b6f52-205">從 XSD 結構描述檔中產生 Common Language Runtime <xref:System.Data.DataSet> 類別。</span><span class="sxs-lookup"><span data-stu-id="b6f52-205">Generates common language runtime <xref:System.Data.DataSet> classes from an XSD schema file.</span></span> <span data-ttu-id="b6f52-206">產生的類別為一般 XML 資料提供了豐富的物件模型。</span><span class="sxs-lookup"><span data-stu-id="b6f52-206">The generated classes provide a rich object model for regular XML data.</span></span>|
|<span data-ttu-id="b6f52-207">XSD 轉換成類別</span><span class="sxs-lookup"><span data-stu-id="b6f52-207">XSD to Classes</span></span>|<span data-ttu-id="b6f52-208">從 XSD 結構描述檔中產生執行階段類別。</span><span class="sxs-lookup"><span data-stu-id="b6f52-208">Generates runtime classes from an XSD schema file.</span></span> <span data-ttu-id="b6f52-209">產生的類別可以配合 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 使用，以讀取和寫入遵循結構描述的 XML 程式碼。</span><span class="sxs-lookup"><span data-stu-id="b6f52-209">The generated classes can be used in conjunction with <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> to read and write XML code that follows the schema.</span></span>|
|<span data-ttu-id="b6f52-210">類別轉換成 XSD</span><span class="sxs-lookup"><span data-stu-id="b6f52-210">Classes to XSD</span></span>| <span data-ttu-id="b6f52-211">從型別或執行階段組件檔中的型別中產生 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="b6f52-211">Generates an XML schema from a type or types in a runtime assembly file.</span></span> <span data-ttu-id="b6f52-212">產生的架構會定義所使用的 XML 格式 <xref:System.Xml.Serialization.XmlSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="b6f52-212">The generated schema defines the XML format used by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|

 <span data-ttu-id="b6f52-213">Xsd.exe 只允許您操作遵循 XML 結構描述定義 (XSD) 語言的 XML 結構描述，而這個 XSD 語言是由全球資訊網協會 (W3C) 所提出的。</span><span class="sxs-lookup"><span data-stu-id="b6f52-213">Xsd.exe only allows you to manipulate XML schemas that follow the XML Schema Definition (XSD) language proposed by the World Wide Web Consortium (W3C).</span></span> <span data-ttu-id="b6f52-214">如需 XML 架構定義建議程式或 XML 標準的詳細資訊，請參閱 <https://w3.org> 。</span><span class="sxs-lookup"><span data-stu-id="b6f52-214">For more information on the XML Schema Definition proposal or the XML standard, see <https://w3.org>.</span></span>

## <a name="setting-options-with-an-xml-file"></a><span data-ttu-id="b6f52-215">設定 XML 檔案的選項</span><span class="sxs-lookup"><span data-stu-id="b6f52-215">Setting Options with an XML File</span></span>

<span data-ttu-id="b6f52-216">使用 `/parameters` 參數時，您可以指定會設定各種選項的單一 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="b6f52-216">By using the `/parameters` switch, you can specify a single XML file that sets various options.</span></span> <span data-ttu-id="b6f52-217">您可以設定的選項會視使用 XSD.exe 工具的方式而定。</span><span class="sxs-lookup"><span data-stu-id="b6f52-217">The options you can set depend on how you are using the XSD.exe tool.</span></span> <span data-ttu-id="b6f52-218">這些選擇包括產生結構描述、產生程式碼檔或產生內含 `DataSet` 功能的程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="b6f52-218">Choices include generating schemas, generating code files, or generating code files that include `DataSet` features.</span></span> <span data-ttu-id="b6f52-219">例如，您可以在產生結構描述時 (但不是在產生程式碼檔案時)，將 `<assembly>` 項目設為可執行檔 (.exe) 或型別程式庫 (.dll) 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="b6f52-219">For example, you can set the `<assembly>` element to the name of an executable (.exe) or type library (.dll) file when generating a schema, but not when generating a code file.</span></span> <span data-ttu-id="b6f52-220">下列 XML 會顯示如何使用 `<generateSchemas>` 項目搭配指定的可執行檔：</span><span class="sxs-lookup"><span data-stu-id="b6f52-220">The following XML shows how to use the `<generateSchemas>` element with a specified executable:</span></span>

```xml
<!-- This is in a file named GenerateSchemas.xml. -->
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateSchemas>
   <assembly>ConsoleApplication1.exe</assembly>
</generateSchemas>
</xsd>
```

<span data-ttu-id="b6f52-221">如果上述 XML 包含在名為 Generateschemas.xml 的檔案中，則請 `/parameters` 在命令提示字元中輸入下列命令，然後按**enter**鍵，以使用參數：</span><span class="sxs-lookup"><span data-stu-id="b6f52-221">If the preceding XML is contained in a file named GenerateSchemas.xml, then use the `/parameters` switch by typing the following at a command prompt and pressing **Enter**:</span></span>

```console
 xsd /p:GenerateSchemas.xml
```

<span data-ttu-id="b6f52-222">換句話說，如果針對在組件中找到的單一型別產生結構描述，就可以使用下列 XML：</span><span class="sxs-lookup"><span data-stu-id="b6f52-222">On the other hand, if you are generating a schema for a single type found in the assembly, you can use the following XML:</span></span>

```xml
<!-- This is in a file named GenerateSchemaFromType.xml. -->
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateSchemas>
   <type>IDItems</type>
</generateSchemas>
</xsd>
```

<span data-ttu-id="b6f52-223">但是若要使用之前的程式碼，您也必須在命令提示字元中提供組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="b6f52-223">But to use preceding code, you must also supply the name of the assembly at the command prompt.</span></span> <span data-ttu-id="b6f52-224">在命令提示字元中輸入下列內容（假設 XML 檔案的名稱為 GenerateSchemaFromType）：</span><span class="sxs-lookup"><span data-stu-id="b6f52-224">Enter the following at a command prompt (presuming the XML file is named GenerateSchemaFromType.xml):</span></span>

```console
xsd /p:GenerateSchemaFromType.xml ConsoleApplication1.exe
```

<span data-ttu-id="b6f52-225">您只能為 `<generateSchemas>` 項目指定下列其中一個選項。</span><span class="sxs-lookup"><span data-stu-id="b6f52-225">You must specify only one of the following options for the `<generateSchemas>` element.</span></span>

|<span data-ttu-id="b6f52-226">元素</span><span class="sxs-lookup"><span data-stu-id="b6f52-226">Element</span></span>|<span data-ttu-id="b6f52-227">描述</span><span class="sxs-lookup"><span data-stu-id="b6f52-227">Description</span></span>|
|-------------|-----------------|
|\<assembly>|<span data-ttu-id="b6f52-228">指定要產生結構描述的組件。</span><span class="sxs-lookup"><span data-stu-id="b6f52-228">Specifies an assembly to generate the schema from.</span></span>|
|\<type>|<span data-ttu-id="b6f52-229">指定在組件中找到的型別，以用於產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="b6f52-229">Specifies a type found in an assembly to generate a schema for.</span></span>|
|\<xml>|<span data-ttu-id="b6f52-230">指定用於產生結構描述的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="b6f52-230">Specifies an XML file to generate a schema for.</span></span>|
|\<xdr>|<span data-ttu-id="b6f52-231">指定用於產生結構描述的 XDR 檔案。</span><span class="sxs-lookup"><span data-stu-id="b6f52-231">Specifies an XDR file to generate a schema for.</span></span>|

<span data-ttu-id="b6f52-232">若要產生程式碼檔，請使用 `<generateClasses>` 項目。</span><span class="sxs-lookup"><span data-stu-id="b6f52-232">To generate a code file, use the `<generateClasses>` element.</span></span> <span data-ttu-id="b6f52-233">下列範例會產生程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="b6f52-233">The following example generates a code file.</span></span> <span data-ttu-id="b6f52-234">請注意，也會顯示兩個屬性，可讓您設定所產生檔案的程式設計語言和命名空間。</span><span class="sxs-lookup"><span data-stu-id="b6f52-234">Note that two attributes are also shown that allow you to set the programming language and namespace of the generated file.</span></span>

```xml
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateClasses language='VB' namespace='Microsoft.Serialization.Examples'/>
</xsd>
<!-- You must supply an .xsd file when typing in the command line.-->
<!-- For example: xsd /p:genClasses mySchema.xsd -->
```

 <span data-ttu-id="b6f52-235">您可以對 `<generateClasses>` 項目設定的選項包括下列各項。</span><span class="sxs-lookup"><span data-stu-id="b6f52-235">Options you can set for the `<generateClasses>` element include the following.</span></span>

|<span data-ttu-id="b6f52-236">元素</span><span class="sxs-lookup"><span data-stu-id="b6f52-236">Element</span></span>|<span data-ttu-id="b6f52-237">描述</span><span class="sxs-lookup"><span data-stu-id="b6f52-237">Description</span></span>|
|-------------|-----------------|
|\<element>|<span data-ttu-id="b6f52-238">指定要產生程式碼之 .xsd 檔案中的項目。</span><span class="sxs-lookup"><span data-stu-id="b6f52-238">Specifies an element in the .xsd file to generate code for.</span></span>|
|\<schemaImporterExtensions>|<span data-ttu-id="b6f52-239">指定衍生自 <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> 類別的型別。</span><span class="sxs-lookup"><span data-stu-id="b6f52-239">Specifies a type derived from the <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> class.</span></span>|
|\<schema>|<span data-ttu-id="b6f52-240">指定用於產生程式碼的 XML 結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="b6f52-240">Specifies a XML Schema file to generate code for.</span></span> <span data-ttu-id="b6f52-241">您可以使用多個專案來指定多個 XML 架構檔案 \<schema> 。</span><span class="sxs-lookup"><span data-stu-id="b6f52-241">Multiple XML Schema files can be specified using multiple \<schema> elements.</span></span>|

<span data-ttu-id="b6f52-242">下表顯示也可以和 `<generateClasses>` 項目搭配使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="b6f52-242">The following table shows the attributes that can also be used with the `<generateClasses>` element.</span></span>

|<span data-ttu-id="b6f52-243">屬性</span><span class="sxs-lookup"><span data-stu-id="b6f52-243">Attribute</span></span>|<span data-ttu-id="b6f52-244">描述</span><span class="sxs-lookup"><span data-stu-id="b6f52-244">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="b6f52-245">語言</span><span class="sxs-lookup"><span data-stu-id="b6f52-245">language</span></span>|<span data-ttu-id="b6f52-246">指定要使用的程式語言。</span><span class="sxs-lookup"><span data-stu-id="b6f52-246">Specifies the programming language to use.</span></span> <span data-ttu-id="b6f52-247">可以選擇 `CS` (C#，此為預設值)、`VB` (Visual Basic)、`JS` (JScript) 或 `VJS` (Visual J#)。</span><span class="sxs-lookup"><span data-stu-id="b6f52-247">Choose from `CS` (C#, the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="b6f52-248">您可以對實作 <xref:System.CodeDom.Compiler.CodeDomProvider> 的類別指定完整名稱。</span><span class="sxs-lookup"><span data-stu-id="b6f52-248">You can also specify a fully qualified name for a class that implements <xref:System.CodeDom.Compiler.CodeDomProvider>.</span></span>|
|<span data-ttu-id="b6f52-249">namespace</span><span class="sxs-lookup"><span data-stu-id="b6f52-249">namespace</span></span>|<span data-ttu-id="b6f52-250">指定產生之程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="b6f52-250">Specifies the namespace for the generated code.</span></span> <span data-ttu-id="b6f52-251">命名空間必須符合 CLR 標準 (例如，沒有空白或反斜線字元)。</span><span class="sxs-lookup"><span data-stu-id="b6f52-251">The namespace must conform to CLR standards (for example, no spaces or backslash characters).</span></span>|
|<span data-ttu-id="b6f52-252">選項</span><span class="sxs-lookup"><span data-stu-id="b6f52-252">options</span></span>|<span data-ttu-id="b6f52-253">下列其中一個值：`none`、`properties` (產生屬性而非公用欄位)、`order` 或 `enableDataBinding` (請參閱先前＜XSD 檔案選項＞一節中的 `/order` 和 `/enableDataBinding` 參數)。</span><span class="sxs-lookup"><span data-stu-id="b6f52-253">One of the following values: `none`, `properties` (generates properties instead of public fields), `order`, or `enableDataBinding` (see the `/order` and `/enableDataBinding` switches in the preceding XSD File Options section.</span></span>|

 <span data-ttu-id="b6f52-254">您也可以使用 `DataSet` 項目，控制產生 `<generateDataSet>` 程式碼的方法。</span><span class="sxs-lookup"><span data-stu-id="b6f52-254">You can also control how `DataSet` code is generated by using the `<generateDataSet>` element.</span></span> <span data-ttu-id="b6f52-255">下列 XML 會指定產生的程式碼使用 `DataSet` 結構（例如 <xref:System.Data.DataTable> 類別）來建立所指定專案的 Visual Basic 程式碼。</span><span class="sxs-lookup"><span data-stu-id="b6f52-255">The following XML specifies that the generated code uses `DataSet` structures (such as the <xref:System.Data.DataTable> class) to create Visual Basic code for a specified element.</span></span> <span data-ttu-id="b6f52-256">所產生的 DataSet 結構將會支援 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="b6f52-256">The generated DataSet structures will support LINQ queries.</span></span>

 ```xml
 <xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
     <generateDataSet language='VB' namespace='Microsoft.Serialization.Examples' enableLinqDataSet='true'>
     </generateDataSet>
 </xsd>
```

<span data-ttu-id="b6f52-257">您可以對 `<generateDataSet>` 項目設定的選項包括下列各項。</span><span class="sxs-lookup"><span data-stu-id="b6f52-257">Options you can set for the `<generateDataSet>` element include the following.</span></span>

|<span data-ttu-id="b6f52-258">元素</span><span class="sxs-lookup"><span data-stu-id="b6f52-258">Element</span></span>|<span data-ttu-id="b6f52-259">描述</span><span class="sxs-lookup"><span data-stu-id="b6f52-259">Description</span></span>|
|-------------|-----------------|
|\<schema>|<span data-ttu-id="b6f52-260">指定用於產生程式碼的 XML 結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="b6f52-260">Specifies an XML Schema file to generate code for.</span></span> <span data-ttu-id="b6f52-261">您可以使用多個專案來指定多個 XML 架構檔案 \<schema> 。</span><span class="sxs-lookup"><span data-stu-id="b6f52-261">Multiple XML Schema files can be specified using multiple \<schema> elements.</span></span>|

 <span data-ttu-id="b6f52-262">下表顯示可以和 `<generateDataSet>` 項目搭配使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="b6f52-262">The following table shows the attributes that can be used with the `<generateDataSet>` element.</span></span>

|<span data-ttu-id="b6f52-263">屬性</span><span class="sxs-lookup"><span data-stu-id="b6f52-263">Attribute</span></span>|<span data-ttu-id="b6f52-264">描述</span><span class="sxs-lookup"><span data-stu-id="b6f52-264">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="b6f52-265">enableLinqDataSet</span><span class="sxs-lookup"><span data-stu-id="b6f52-265">enableLinqDataSet</span></span>|<span data-ttu-id="b6f52-266">指定產生的 DataSet 可使用 LINQ to DataSet 查詢。</span><span class="sxs-lookup"><span data-stu-id="b6f52-266">Specifies that the generated DataSet can be queried against using LINQ to DataSet.</span></span> <span data-ttu-id="b6f52-267">預設值為 false。</span><span class="sxs-lookup"><span data-stu-id="b6f52-267">The default value is false.</span></span>|
|<span data-ttu-id="b6f52-268">語言</span><span class="sxs-lookup"><span data-stu-id="b6f52-268">language</span></span>|<span data-ttu-id="b6f52-269">指定要使用的程式語言。</span><span class="sxs-lookup"><span data-stu-id="b6f52-269">Specifies the programming language to use.</span></span> <span data-ttu-id="b6f52-270">可以選擇 `CS` (C#，此為預設值)、`VB` (Visual Basic)、`JS` (JScript) 或 `VJS` (Visual J#)。</span><span class="sxs-lookup"><span data-stu-id="b6f52-270">Choose from `CS` (C#, the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="b6f52-271">您可以對實作 <xref:System.CodeDom.Compiler.CodeDomProvider> 的類別指定完整名稱。</span><span class="sxs-lookup"><span data-stu-id="b6f52-271">You can also specify a fully qualified name for a class that implements <xref:System.CodeDom.Compiler.CodeDomProvider>.</span></span>|
|<span data-ttu-id="b6f52-272">namespace</span><span class="sxs-lookup"><span data-stu-id="b6f52-272">namespace</span></span>|<span data-ttu-id="b6f52-273">指定產生之程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="b6f52-273">Specifies the namespace for the generated code.</span></span> <span data-ttu-id="b6f52-274">命名空間必須符合 CLR 標準 (例如，沒有空白或反斜線字元)。</span><span class="sxs-lookup"><span data-stu-id="b6f52-274">The namespace must conform to CLR standards (for example, no spaces or backslash characters).</span></span>|

 <span data-ttu-id="b6f52-275">在最上層 `<xsd>` 項目中有一些您可以設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="b6f52-275">There are attributes that you can set on the top level `<xsd>` element.</span></span> <span data-ttu-id="b6f52-276">這些選項可以和任何子項目搭配使用 (`<generateSchemas>`、`<generateClasses>` 或 `<generateDataSet>`)。</span><span class="sxs-lookup"><span data-stu-id="b6f52-276">These options can be used with any of the child elements (`<generateSchemas>`, `<generateClasses>` or `<generateDataSet>`).</span></span> <span data-ttu-id="b6f52-277">下列 XML 程式碼會對名為 "IDItems" 的項目，在名為 "MyOutputDirectory" 的輸出目錄中產生程式碼。</span><span class="sxs-lookup"><span data-stu-id="b6f52-277">The following XML code generates code for an element named "IDItems" in the output directory named "MyOutputDirectory".</span></span>

```xml
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/' output='MyOutputDirectory'>
<generateClasses>
    <element>IDItems</element>
</generateClasses>
</xsd>
```

<span data-ttu-id="b6f52-278">下表顯示也可以和 `<xsd>` 項目搭配使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="b6f52-278">The following table shows the attributes that can also be used with the `<xsd>` element.</span></span>

|<span data-ttu-id="b6f52-279">屬性</span><span class="sxs-lookup"><span data-stu-id="b6f52-279">Attribute</span></span>|<span data-ttu-id="b6f52-280">描述</span><span class="sxs-lookup"><span data-stu-id="b6f52-280">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="b6f52-281">output</span><span class="sxs-lookup"><span data-stu-id="b6f52-281">output</span></span>|<span data-ttu-id="b6f52-282">將放置產生的結構描述或程式碼檔的目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="b6f52-282">The name of a directory where the generated schema or code file will be placed.</span></span>|
|<span data-ttu-id="b6f52-283">nologo</span><span class="sxs-lookup"><span data-stu-id="b6f52-283">nologo</span></span>|<span data-ttu-id="b6f52-284">隱藏產品啟始畫面。</span><span class="sxs-lookup"><span data-stu-id="b6f52-284">Suppresses the banner.</span></span> <span data-ttu-id="b6f52-285">設為 `true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="b6f52-285">Set to `true` or `false`.</span></span>|
|<span data-ttu-id="b6f52-286">help</span><span class="sxs-lookup"><span data-stu-id="b6f52-286">help</span></span>|<span data-ttu-id="b6f52-287">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="b6f52-287">Displays command syntax and options for the tool.</span></span> <span data-ttu-id="b6f52-288">設為 `true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="b6f52-288">Set to `true` or `false`.</span></span>|

## <a name="examples"></a><span data-ttu-id="b6f52-289">範例</span><span class="sxs-lookup"><span data-stu-id="b6f52-289">Examples</span></span>
 <span data-ttu-id="b6f52-290">下列命令會從 `myFile.xdr` 產生 XML 結構描述，並將它儲存到目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="b6f52-290">The following command generates an XML schema from `myFile.xdr` and saves it to the current directory.</span></span>

```console
xsd myFile.xdr
```

<span data-ttu-id="b6f52-291">下列命令會從 `myFile.xml` 產生 XML 結構描述，並將它儲存到指定的目錄。</span><span class="sxs-lookup"><span data-stu-id="b6f52-291">The following command generates an XML schema from `myFile.xml` and saves it to the specified directory.</span></span>

```console
xsd myFile.xml /outputdir:myOutputDir
```

<span data-ttu-id="b6f52-292">下列命令會產生對應到以 C# 語言指定之結構描述的資料集，並在目前的目錄中將它儲存為 `XSDSchemaFile.cs`。</span><span class="sxs-lookup"><span data-stu-id="b6f52-292">The following command generates a data set that corresponds to the specified schema in the C# language and saves it as `XSDSchemaFile.cs` in the current directory.</span></span>

```console
xsd /dataset /language:CS XSDSchemaFile.xsd
```

<span data-ttu-id="b6f52-293">下列命令會對 `myAssembly.dll` 組件中的所有型別產生 XML 結構描述，並在目前的目錄中將它們儲存為 `schema0.xsd`。</span><span class="sxs-lookup"><span data-stu-id="b6f52-293">The following command generates XML schemas for all types in the assembly `myAssembly.dll` and saves them as `schema0.xsd` in the current directory.</span></span>

```console
xsd myAssembly.dll
```

## <a name="see-also"></a><span data-ttu-id="b6f52-294">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6f52-294">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
- [<span data-ttu-id="b6f52-295">工具</span><span class="sxs-lookup"><span data-stu-id="b6f52-295">Tools</span></span>](../../framework/tools/index.md)
- [<span data-ttu-id="b6f52-296">命令提示字元</span><span class="sxs-lookup"><span data-stu-id="b6f52-296">Command Prompts</span></span>](../../framework/tools/developer-command-prompt-for-vs.md)
- [<span data-ttu-id="b6f52-297">LINQ to DataSet 概觀</span><span class="sxs-lookup"><span data-stu-id="b6f52-297">LINQ to DataSet Overview</span></span>](../../framework/data/adonet/linq-to-dataset-overview.md)
- [<span data-ttu-id="b6f52-298">查詢具類型資料集</span><span class="sxs-lookup"><span data-stu-id="b6f52-298">Querying Typed DataSets</span></span>](../../framework/data/adonet/querying-typed-datasets.md)
- [<span data-ttu-id="b6f52-299">LINQ （語言整合式查詢）（c #）</span><span class="sxs-lookup"><span data-stu-id="b6f52-299">LINQ (Language-Integrated Query) (C#)</span></span>](../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="b6f52-300">LINQ （語言整合式查詢）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="b6f52-300">LINQ (Language-Integrated Query) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/index.md)
