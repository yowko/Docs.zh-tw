---
title: XML Schema Definition Tool (Xsd.exe)
ms.date: 03/30/2017
ms.assetid: a6e6e65c-347f-4494-9457-653bf29baac2
ms.openlocfilehash: 6ec99e77db4215184547ea2bbbe0d1ff8ad3c286
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389765"
---
# <a name="xml-schema-definition-tool-xsdexe"></a><span data-ttu-id="c1f40-102">XML Schema Definition Tool (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="c1f40-102">XML Schema Definition Tool (Xsd.exe)</span></span>

<span data-ttu-id="c1f40-103">XML 結構描述定義工具 (Xsd.exe) 可以從 XDR、XML 和 XSD 檔案或從執行階段組件的類別中，產生 XML 結構描述或 Common Language Runtime 類別。</span><span class="sxs-lookup"><span data-stu-id="c1f40-103">The XML Schema Definition (Xsd.exe) tool generates XML schema or common language runtime classes from XDR, XML, and XSD files, or from classes in a runtime assembly.</span></span>

<span data-ttu-id="c1f40-104">XML 架構定義工具（Xsd.exe）通常可以在下列路徑中找到： </span><span class="sxs-lookup"><span data-stu-id="c1f40-104">The XML Schema Definition tool (Xsd.exe) usually can be found in the following path:</span></span>\
<span data-ttu-id="c1f40-105">_C：\\Program Files （x86）\\Microsoft sdk\\Windows\\{version}\\bin\\NETFX {version} 工具\\_</span><span class="sxs-lookup"><span data-stu-id="c1f40-105">_C:\\Program Files (x86)\\Microsoft SDKs\\Windows\\{version}\\bin\\NETFX {version} Tools\\_</span></span>

## <a name="syntax"></a><span data-ttu-id="c1f40-106">語法</span><span class="sxs-lookup"><span data-stu-id="c1f40-106">Syntax</span></span>

<span data-ttu-id="c1f40-107">從命令列執行工具。</span><span class="sxs-lookup"><span data-stu-id="c1f40-107">Run the tool from the command line.</span></span>

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
> <span data-ttu-id="c1f40-108">若要讓 .NET Framework 工具正常運作，您必須正確`Path`地`Include`設定、 `Lib`和環境變數。</span><span class="sxs-lookup"><span data-stu-id="c1f40-108">For .NET Framework tools to function properly, you must set your `Path`, `Include`, and `Lib` environment variables correctly.</span></span> <span data-ttu-id="c1f40-109">執行位於 \<SDK>\v2.0\Bin 目錄中的 SDKVars.bat，即可設定這些環境變數。</span><span class="sxs-lookup"><span data-stu-id="c1f40-109">Set these environment variables by running SDKVars.bat, which is located in the \<SDK>\v2.0\Bin directory.</span></span> <span data-ttu-id="c1f40-110">SDKVars.bat 必須在每一個命令提示字元中執行。</span><span class="sxs-lookup"><span data-stu-id="c1f40-110">SDKVars.bat must be executed in every command shell.</span></span>

## <a name="argument"></a><span data-ttu-id="c1f40-111">引數</span><span class="sxs-lookup"><span data-stu-id="c1f40-111">Argument</span></span>

|<span data-ttu-id="c1f40-112">引數</span><span class="sxs-lookup"><span data-stu-id="c1f40-112">Argument</span></span>|<span data-ttu-id="c1f40-113">描述</span><span class="sxs-lookup"><span data-stu-id="c1f40-113">Description</span></span>|
|--------------|-----------------|
|<span data-ttu-id="c1f40-114">*副檔名*</span><span class="sxs-lookup"><span data-stu-id="c1f40-114">*file.extension*</span></span>|<span data-ttu-id="c1f40-115">指定要轉換的輸入檔。</span><span class="sxs-lookup"><span data-stu-id="c1f40-115">Specifies the input file to convert.</span></span> <span data-ttu-id="c1f40-116">您必須將此延伸模組指定為下列其中一項： xdr、.xml、.xsd、.dll 或 .exe。</span><span class="sxs-lookup"><span data-stu-id="c1f40-116">You must specify the extension as one of the following: .xdr, .xml, .xsd, .dll, or .exe.</span></span><br /><br /> <span data-ttu-id="c1f40-117">如果指定 XDR 結構描述檔 (副檔名為 .xdr )，Xsd.exe 會將 XDR 結構描述轉換成 XSD 結構描述。</span><span class="sxs-lookup"><span data-stu-id="c1f40-117">If you specify an XDR schema file (.xdr extension), Xsd.exe converts the XDR schema to an XSD schema.</span></span> <span data-ttu-id="c1f40-118">輸出檔有和 XDR 結構描述一樣的名稱，但是具有 .xsd 副檔名。</span><span class="sxs-lookup"><span data-stu-id="c1f40-118">The output file has the same name as the XDR schema, but with the .xsd extension.</span></span><br /><br /> <span data-ttu-id="c1f40-119">如果指定 XML 檔 (副檔名為 .xml )，Xsd.exe 會從檔案中的資料推斷結構描述，然後產生 XSD 結構描述。</span><span class="sxs-lookup"><span data-stu-id="c1f40-119">If you specify an XML file (.xml extension), Xsd.exe infers a schema from the data in the file and produces an XSD schema.</span></span> <span data-ttu-id="c1f40-120">輸出檔有和 XML 檔一樣的名稱，但是具有 .xsd 副檔名。</span><span class="sxs-lookup"><span data-stu-id="c1f40-120">The output file has the same name as the XML file, but with the .xsd extension.</span></span><br /><br /> <span data-ttu-id="c1f40-121">如果指定 XML 結構描述檔 (.xsd 副檔名)，Xsd.exe 會產生對應到 XML 結構描述之 Runtime 物件的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="c1f40-121">If you specify an XML schema file (.xsd extension), Xsd.exe generates source code for runtime objects that correspond to the XML schema.</span></span><br /><br /> <span data-ttu-id="c1f40-122">如果指定執行階段組件檔 (.exe 或 .dll 副檔名)，Xsd.exe 會產生該組件中一個或多個型別的結構描述。</span><span class="sxs-lookup"><span data-stu-id="c1f40-122">If you specify a runtime assembly file (.exe or .dll extension), Xsd.exe generates schemas for one or more types in that assembly.</span></span> <span data-ttu-id="c1f40-123">您可以使用 `/type` 選項來指定要產生結構描述的型別。</span><span class="sxs-lookup"><span data-stu-id="c1f40-123">You can use the `/type` option to specify the types for which to generate schemas.</span></span> <span data-ttu-id="c1f40-124">輸出結構描述被命名為 schema0.xsd、schema1.xsd 等等。</span><span class="sxs-lookup"><span data-stu-id="c1f40-124">The output schemas are named schema0.xsd, schema1.xsd, and so on.</span></span> <span data-ttu-id="c1f40-125">只有在指定的型別使用 `XMLRoot` 自訂屬性來指定命名空間 (Namespace) 時，Xsd.exe 才能產生多個結構描述。</span><span class="sxs-lookup"><span data-stu-id="c1f40-125">Xsd.exe produces multiple schemas only if the given types specify a namespace using the `XMLRoot` custom attribute.</span></span>|

## <a name="general-options"></a><span data-ttu-id="c1f40-126">一般選項</span><span class="sxs-lookup"><span data-stu-id="c1f40-126">General Options</span></span>

|<span data-ttu-id="c1f40-127">選項</span><span class="sxs-lookup"><span data-stu-id="c1f40-127">Option</span></span>|<span data-ttu-id="c1f40-128">說明</span><span class="sxs-lookup"><span data-stu-id="c1f40-128">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="c1f40-129">**/h\[elp\]**</span><span class="sxs-lookup"><span data-stu-id="c1f40-129">**/h\[elp\]**</span></span>|<span data-ttu-id="c1f40-130">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="c1f40-130">Displays command syntax and options for the tool.</span></span>|
|<span data-ttu-id="c1f40-131">**/o\[utputdir\]：**_directory_</span><span class="sxs-lookup"><span data-stu-id="c1f40-131">**/o\[utputdir\]:**_directory_</span></span>|<span data-ttu-id="c1f40-132">指定輸出檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="c1f40-132">Specifies the directory for output files.</span></span> <span data-ttu-id="c1f40-133">這個引數只可以使用一次。</span><span class="sxs-lookup"><span data-stu-id="c1f40-133">This argument can appear only once.</span></span> <span data-ttu-id="c1f40-134">預設值是目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="c1f40-134">The default is the current directory.</span></span>|
|<span data-ttu-id="c1f40-135">**/?**</span><span class="sxs-lookup"><span data-stu-id="c1f40-135">**/?**</span></span>|<span data-ttu-id="c1f40-136">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="c1f40-136">Displays command syntax and options for the tool.</span></span>|
|<span data-ttu-id="c1f40-137">**/p\[arameters\]：**_file .xml_</span><span class="sxs-lookup"><span data-stu-id="c1f40-137">**/p\[arameters\]:**_file.xml_</span></span>|<span data-ttu-id="c1f40-138">從指定的 .xml 檔案，讀取各種作業模式的選項。</span><span class="sxs-lookup"><span data-stu-id="c1f40-138">Read options for various operation modes from the specified .xml file.</span></span> <span data-ttu-id="c1f40-139">簡短形式為 `/p:`。</span><span class="sxs-lookup"><span data-stu-id="c1f40-139">The short form is `/p:`.</span></span> <span data-ttu-id="c1f40-140">如需詳細資訊，請參閱[備註](#remarks)一節。</span><span class="sxs-lookup"><span data-stu-id="c1f40-140">For more information, see the [Remarks](#remarks) section.</span></span>|

## <a name="xsd-file-options"></a><span data-ttu-id="c1f40-141">XSD 檔案選項</span><span class="sxs-lookup"><span data-stu-id="c1f40-141">XSD File Options</span></span>
 <span data-ttu-id="c1f40-142">您只能為 .xsd 檔指定下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="c1f40-142">You must specify only one of the following options for .xsd files.</span></span>

|<span data-ttu-id="c1f40-143">選項</span><span class="sxs-lookup"><span data-stu-id="c1f40-143">Option</span></span>|<span data-ttu-id="c1f40-144">說明</span><span class="sxs-lookup"><span data-stu-id="c1f40-144">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="c1f40-145">**/c\[lasses\]**</span><span class="sxs-lookup"><span data-stu-id="c1f40-145">**/c\[lasses\]**</span></span>|<span data-ttu-id="c1f40-146">產生對應到指定的結構描述的類別。</span><span class="sxs-lookup"><span data-stu-id="c1f40-146">Generates classes that correspond to the specified schema.</span></span> <span data-ttu-id="c1f40-147">若要將 XML 資料讀入物件，請使用 <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="c1f40-147">To read XML data into the object, use the <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>|
|<span data-ttu-id="c1f40-148">**/d\[ataset\]**</span><span class="sxs-lookup"><span data-stu-id="c1f40-148">**/d\[ataset\]**</span></span>|<span data-ttu-id="c1f40-149">產生衍生自 <xref:System.Data.DataSet> 的類別，對應到指定的結構描述。</span><span class="sxs-lookup"><span data-stu-id="c1f40-149">Generates a class derived from <xref:System.Data.DataSet> that corresponds to the specified schema.</span></span> <span data-ttu-id="c1f40-150">若要將 XML 資料讀入衍生類別，請使用 <xref:System.Data.DataSet.ReadXml%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="c1f40-150">To read XML data into the derived class, use the <xref:System.Data.DataSet.ReadXml%2A?displayProperty=nameWithType> method.</span></span>|

 <span data-ttu-id="c1f40-151">您也可以為 .xsd 檔指定下列任何選項：</span><span class="sxs-lookup"><span data-stu-id="c1f40-151">You can also specify any of the following options for .xsd files.</span></span>

|<span data-ttu-id="c1f40-152">選項</span><span class="sxs-lookup"><span data-stu-id="c1f40-152">Option</span></span>|<span data-ttu-id="c1f40-153">說明</span><span class="sxs-lookup"><span data-stu-id="c1f40-153">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="c1f40-154">**/e\[lement\]：**_元素_</span><span class="sxs-lookup"><span data-stu-id="c1f40-154">**/e\[lement\]:**_element_</span></span>|<span data-ttu-id="c1f40-155">指定所要產生程式碼的結構描述中的項目。</span><span class="sxs-lookup"><span data-stu-id="c1f40-155">Specifies the element in the schema to generate code for.</span></span> <span data-ttu-id="c1f40-156">根據預設，會輸入所有項目。</span><span class="sxs-lookup"><span data-stu-id="c1f40-156">By default all elements are typed.</span></span> <span data-ttu-id="c1f40-157">您可以多次指定這個引數。</span><span class="sxs-lookup"><span data-stu-id="c1f40-157">You can specify this argument more than once.</span></span>|
|<span data-ttu-id="c1f40-158">**/enableDataBinding**</span><span class="sxs-lookup"><span data-stu-id="c1f40-158">**/enableDataBinding**</span></span>|<span data-ttu-id="c1f40-159">在所有產生的型別上實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面，以啟用資料繫結 (Data Binding)。</span><span class="sxs-lookup"><span data-stu-id="c1f40-159">Implements the <xref:System.ComponentModel.INotifyPropertyChanged> interface on all generated types to enable data binding.</span></span> <span data-ttu-id="c1f40-160">簡短形式為 `/edb`。</span><span class="sxs-lookup"><span data-stu-id="c1f40-160">The short form is `/edb`.</span></span>|
|<span data-ttu-id="c1f40-161">**/enableLinqDataSet**</span><span class="sxs-lookup"><span data-stu-id="c1f40-161">**/enableLinqDataSet**</span></span>|<span data-ttu-id="c1f40-162">（簡短形式： `/eld`.）指定所產生的資料集可以使用 LINQ to DataSet 來查詢。</span><span class="sxs-lookup"><span data-stu-id="c1f40-162">(Short form: `/eld`.) Specifies that the generated DataSet can be queried against using LINQ to DataSet.</span></span> <span data-ttu-id="c1f40-163">如果也指定了 /dataset 選項，就會使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="c1f40-163">This option is used when the /dataset option is also specified.</span></span> <span data-ttu-id="c1f40-164">如需詳細資訊，請參閱 [LINQ to DataSet 概觀](../../../docs/framework/data/adonet/linq-to-dataset-overview.md)和[查詢具類型資料集](../../../docs/framework/data/adonet/querying-typed-datasets.md)。</span><span class="sxs-lookup"><span data-stu-id="c1f40-164">For more information, see [LINQ to DataSet Overview](../../../docs/framework/data/adonet/linq-to-dataset-overview.md) and [Querying Typed DataSets](../../../docs/framework/data/adonet/querying-typed-datasets.md).</span></span> <span data-ttu-id="c1f40-165">如需使用 LINQ 的一般資訊，請參閱[語言整合式查詢（linq）-c #](../../csharp/programming-guide/concepts/linq/index.md)或[語言整合查詢（linq）-Visual Basic](../../visual-basic/programming-guide/concepts/linq/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c1f40-165">For general information about using LINQ, see [Language-Integrated Query (LINQ) - C#](../../csharp/programming-guide/concepts/linq/index.md) or [Language-Integrated Query (LINQ) - Visual Basic](../../visual-basic/programming-guide/concepts/linq/index.md).</span></span>|
|<span data-ttu-id="c1f40-166">**/f\[ields\]**</span><span class="sxs-lookup"><span data-stu-id="c1f40-166">**/f\[ields\]**</span></span>|<span data-ttu-id="c1f40-167">產生欄位，而不是產生屬性。</span><span class="sxs-lookup"><span data-stu-id="c1f40-167">Generates fields instead of properties.</span></span> <span data-ttu-id="c1f40-168">根據預設，會產生屬性。</span><span class="sxs-lookup"><span data-stu-id="c1f40-168">By default, properties are generated.</span></span>|
|<span data-ttu-id="c1f40-169">**/l\[anguage\]：**_language_</span><span class="sxs-lookup"><span data-stu-id="c1f40-169">**/l\[anguage\]:**_language_</span></span>|<span data-ttu-id="c1f40-170">指定要使用的程式語言。</span><span class="sxs-lookup"><span data-stu-id="c1f40-170">Specifies the programming language to use.</span></span> <span data-ttu-id="c1f40-171">可以選擇 `CS` (C#，此為預設值)、`VB` (Visual Basic)、`JS` (JScript) 或 `VJS` (Visual J#)。</span><span class="sxs-lookup"><span data-stu-id="c1f40-171">Choose from `CS` (C#, which is the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="c1f40-172">您也可以對實作 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> 的類別指定完整名稱。</span><span class="sxs-lookup"><span data-stu-id="c1f40-172">You can also specify a fully qualified name for a class implementing <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType></span></span>|
|<span data-ttu-id="c1f40-173">**/n\[amespace\]：**_命名空間_</span><span class="sxs-lookup"><span data-stu-id="c1f40-173">**/n\[amespace\]:**_namespace_</span></span>|<span data-ttu-id="c1f40-174">指定產生的型別的執行階段命名空間。</span><span class="sxs-lookup"><span data-stu-id="c1f40-174">Specifies the runtime namespace for the generated types.</span></span> <span data-ttu-id="c1f40-175">預設命名空間是 `Schemas`。</span><span class="sxs-lookup"><span data-stu-id="c1f40-175">The default namespace is `Schemas`.</span></span>|
|<span data-ttu-id="c1f40-176">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="c1f40-176">**/nologo**</span></span>|<span data-ttu-id="c1f40-177">隱藏產品啟始畫面。</span><span class="sxs-lookup"><span data-stu-id="c1f40-177">Suppresses the banner.</span></span>|
|<span data-ttu-id="c1f40-178">**/order**</span><span class="sxs-lookup"><span data-stu-id="c1f40-178">**/order**</span></span>|<span data-ttu-id="c1f40-179">在所有物件成員上產生明確順序識別項。</span><span class="sxs-lookup"><span data-stu-id="c1f40-179">Generates explicit order identifiers on all particle members.</span></span>|
|<span data-ttu-id="c1f40-180">\*\* \[/o\]內容：\*\*_directoryName_</span><span class="sxs-lookup"><span data-stu-id="c1f40-180">**/o\[ut\]:**_directoryName_</span></span>|<span data-ttu-id="c1f40-181">指定要在其中放置檔案的輸出目錄。</span><span class="sxs-lookup"><span data-stu-id="c1f40-181">Specifies the output directory to place the files in.</span></span> <span data-ttu-id="c1f40-182">預設值是目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="c1f40-182">The default is the current directory.</span></span>|
|<span data-ttu-id="c1f40-183">**/u\[ri\]：**_uri_</span><span class="sxs-lookup"><span data-stu-id="c1f40-183">**/u\[ri\]:**_uri_</span></span>|<span data-ttu-id="c1f40-184">指定所要產生程式碼的結構描述中項目的 URI。</span><span class="sxs-lookup"><span data-stu-id="c1f40-184">Specifies the URI for the elements in the schema to generate code for.</span></span> <span data-ttu-id="c1f40-185">這個 URI 如果存在，會套用到所有以 `/element` 選項指定的項目。</span><span class="sxs-lookup"><span data-stu-id="c1f40-185">This URI, if present, applies to all elements specified with the `/element` option.</span></span>|

## <a name="dll-and-exe-file-options"></a><span data-ttu-id="c1f40-186">DLL 和 EXE 檔案選項</span><span class="sxs-lookup"><span data-stu-id="c1f40-186">DLL and EXE File Options</span></span>

|<span data-ttu-id="c1f40-187">選項</span><span class="sxs-lookup"><span data-stu-id="c1f40-187">Option</span></span>|<span data-ttu-id="c1f40-188">說明</span><span class="sxs-lookup"><span data-stu-id="c1f40-188">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="c1f40-189">**/t\[\]**_類型名稱： typename_</span><span class="sxs-lookup"><span data-stu-id="c1f40-189">**/t\[ype\]:**_typename_</span></span>|<span data-ttu-id="c1f40-190">指定所要建立結構描述的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="c1f40-190">Specifies the name of the type to create a schema for.</span></span> <span data-ttu-id="c1f40-191">您可以指定多個型別引數。</span><span class="sxs-lookup"><span data-stu-id="c1f40-191">You can specify multiple type arguments.</span></span> <span data-ttu-id="c1f40-192">如果 *typename* 沒有指定命名空間，Xsd.exe 會以指定的類型比對組件中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="c1f40-192">If *typename* does not specify a namespace, Xsd.exe matches all types in the assembly with the specified type.</span></span> <span data-ttu-id="c1f40-193">如果 *typename* 指定命名空間，只有該類型會被比對。</span><span class="sxs-lookup"><span data-stu-id="c1f40-193">If *typename* specifies a namespace, only that type is matched.</span></span> <span data-ttu-id="c1f40-194">如果 *typename* 結尾為星號字元 (\*)，則工具會比對 \* 之前以這個字串為開頭的所有類型。</span><span class="sxs-lookup"><span data-stu-id="c1f40-194">If *typename* ends with an asterisk character (\*), the tool matches all types that start with the string preceding the \*.</span></span> <span data-ttu-id="c1f40-195">如果省略 `/type` 選項，Xsd.exe 會產生組件中所有型別的結構描述。</span><span class="sxs-lookup"><span data-stu-id="c1f40-195">If you omit the `/type` option, Xsd.exe generates schemas for all types in the assembly.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c1f40-196">備註</span><span class="sxs-lookup"><span data-stu-id="c1f40-196">Remarks</span></span>

<span data-ttu-id="c1f40-197">下表列出 Xsd.exe 執行的作業。</span><span class="sxs-lookup"><span data-stu-id="c1f40-197">The following table shows the operations that Xsd.exe performs.</span></span>

| | |
|------------|-----------------|
|<span data-ttu-id="c1f40-198">XDR 轉換成 XSD</span><span class="sxs-lookup"><span data-stu-id="c1f40-198">XDR to XSD</span></span>|<span data-ttu-id="c1f40-199">從 XML-Data-Reduced 結構描述檔中產生 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="c1f40-199">Generates an XML schema from an XML-Data-Reduced schema file.</span></span> <span data-ttu-id="c1f40-200">XDR 是早期 XML 架構的結構描述。</span><span class="sxs-lookup"><span data-stu-id="c1f40-200">XDR is an early XML-based schema format.</span></span>|
|<span data-ttu-id="c1f40-201">XML 轉換成 XSD</span><span class="sxs-lookup"><span data-stu-id="c1f40-201">XML to XSD</span></span>|<span data-ttu-id="c1f40-202">從 XML 檔案中產生 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="c1f40-202">Generates an XML schema from an XML file.</span></span>|
|<span data-ttu-id="c1f40-203">XSD 轉換成 DataSet</span><span class="sxs-lookup"><span data-stu-id="c1f40-203">XSD to DataSet</span></span>|<span data-ttu-id="c1f40-204">從 XSD 結構描述檔中產生 Common Language Runtime <xref:System.Data.DataSet> 類別。</span><span class="sxs-lookup"><span data-stu-id="c1f40-204">Generates common language runtime <xref:System.Data.DataSet> classes from an XSD schema file.</span></span> <span data-ttu-id="c1f40-205">產生的類別為一般 XML 資料提供了豐富的物件模型。</span><span class="sxs-lookup"><span data-stu-id="c1f40-205">The generated classes provide a rich object model for regular XML data.</span></span>|
|<span data-ttu-id="c1f40-206">XSD 轉換成類別</span><span class="sxs-lookup"><span data-stu-id="c1f40-206">XSD to Classes</span></span>|<span data-ttu-id="c1f40-207">從 XSD 結構描述檔中產生執行階段類別。</span><span class="sxs-lookup"><span data-stu-id="c1f40-207">Generates runtime classes from an XSD schema file.</span></span> <span data-ttu-id="c1f40-208">產生的類別可以配合 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 使用，以讀取和寫入遵循結構描述的 XML 程式碼。</span><span class="sxs-lookup"><span data-stu-id="c1f40-208">The generated classes can be used in conjunction with <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> to read and write XML code that follows the schema.</span></span>|
|<span data-ttu-id="c1f40-209">類別轉換成 XSD</span><span class="sxs-lookup"><span data-stu-id="c1f40-209">Classes to XSD</span></span>| <span data-ttu-id="c1f40-210">從型別或執行階段組件檔中的型別中產生 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="c1f40-210">Generates an XML schema from a type or types in a runtime assembly file.</span></span> <span data-ttu-id="c1f40-211">產生的架構會定義所<xref:System.Xml.Serialization.XmlSerializer>使用的 XML 格式。</span><span class="sxs-lookup"><span data-stu-id="c1f40-211">The generated schema defines the XML format used by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|

 <span data-ttu-id="c1f40-212">Xsd.exe 只允許您操作遵循 XML 結構描述定義 (XSD) 語言的 XML 結構描述，而這個 XSD 語言是由全球資訊網協會 (W3C) 所提出的。</span><span class="sxs-lookup"><span data-stu-id="c1f40-212">Xsd.exe only allows you to manipulate XML schemas that follow the XML Schema Definition (XSD) language proposed by the World Wide Web Consortium (W3C).</span></span> <span data-ttu-id="c1f40-213">如需 XML 架構定義建議程式或 XML 標準的詳細資訊，請<https://w3.org>參閱。</span><span class="sxs-lookup"><span data-stu-id="c1f40-213">For more information on the XML Schema Definition proposal or the XML standard, see <https://w3.org>.</span></span>

## <a name="setting-options-with-an-xml-file"></a><span data-ttu-id="c1f40-214">設定 XML 檔案的選項</span><span class="sxs-lookup"><span data-stu-id="c1f40-214">Setting Options with an XML File</span></span>

<span data-ttu-id="c1f40-215">使用 `/parameters` 參數時，您可以指定會設定各種選項的單一 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="c1f40-215">By using the `/parameters` switch, you can specify a single XML file that sets various options.</span></span> <span data-ttu-id="c1f40-216">您可以設定的選項會視使用 XSD.exe 工具的方式而定。</span><span class="sxs-lookup"><span data-stu-id="c1f40-216">The options you can set depend on how you are using the XSD.exe tool.</span></span> <span data-ttu-id="c1f40-217">這些選擇包括產生結構描述、產生程式碼檔或產生內含 `DataSet` 功能的程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="c1f40-217">Choices include generating schemas, generating code files, or generating code files that include `DataSet` features.</span></span> <span data-ttu-id="c1f40-218">例如，您可以在產生結構描述時 (但不是在產生程式碼檔案時)，將 `<assembly>` 項目設為可執行檔 (.exe) 或型別程式庫 (.dll) 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="c1f40-218">For example, you can set the `<assembly>` element to the name of an executable (.exe) or type library (.dll) file when generating a schema, but not when generating a code file.</span></span> <span data-ttu-id="c1f40-219">下列 XML 會顯示如何使用 `<generateSchemas>` 項目搭配指定的可執行檔：</span><span class="sxs-lookup"><span data-stu-id="c1f40-219">The following XML shows how to use the `<generateSchemas>` element with a specified executable:</span></span>

```xml
<!-- This is in a file named GenerateSchemas.xml. -->
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateSchemas>
   <assembly>ConsoleApplication1.exe</assembly>
</generateSchemas>
</xsd>
```

<span data-ttu-id="c1f40-220">如果上述 XML 包含在名為 Generateschemas.xml 的檔案中，則請在命令提示`/parameters`字元中輸入下列命令，然後按**enter**鍵，以使用參數：</span><span class="sxs-lookup"><span data-stu-id="c1f40-220">If the preceding XML is contained in a file named GenerateSchemas.xml, then use the `/parameters` switch by typing the following at a command prompt and pressing **Enter**:</span></span>

```console
 xsd /p:GenerateSchemas.xml
```

<span data-ttu-id="c1f40-221">換句話說，如果針對在組件中找到的單一型別產生結構描述，就可以使用下列 XML：</span><span class="sxs-lookup"><span data-stu-id="c1f40-221">On the other hand, if you are generating a schema for a single type found in the assembly, you can use the following XML:</span></span>

```xml
<!-- This is in a file named GenerateSchemaFromType.xml. -->
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateSchemas>
   <type>IDItems</type>
</generateSchemas>
</xsd>
```

<span data-ttu-id="c1f40-222">但是若要使用之前的程式碼，您也必須在命令提示字元中提供組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="c1f40-222">But to use preceding code, you must also supply the name of the assembly at the command prompt.</span></span> <span data-ttu-id="c1f40-223">在命令提示字元中輸入下列內容（假設 XML 檔案的名稱為 GenerateSchemaFromType）：</span><span class="sxs-lookup"><span data-stu-id="c1f40-223">Enter the following at a command prompt (presuming the XML file is named GenerateSchemaFromType.xml):</span></span>

```console
xsd /p:GenerateSchemaFromType.xml ConsoleApplication1.exe
```

<span data-ttu-id="c1f40-224">您只能為 `<generateSchemas>` 項目指定下列其中一個選項。</span><span class="sxs-lookup"><span data-stu-id="c1f40-224">You must specify only one of the following options for the `<generateSchemas>` element.</span></span>

|<span data-ttu-id="c1f40-225">元素</span><span class="sxs-lookup"><span data-stu-id="c1f40-225">Element</span></span>|<span data-ttu-id="c1f40-226">描述</span><span class="sxs-lookup"><span data-stu-id="c1f40-226">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="c1f40-227">\<assembly></span><span class="sxs-lookup"><span data-stu-id="c1f40-227">\<assembly></span></span>|<span data-ttu-id="c1f40-228">指定要產生結構描述的組件。</span><span class="sxs-lookup"><span data-stu-id="c1f40-228">Specifies an assembly to generate the schema from.</span></span>|
|<span data-ttu-id="c1f40-229">\<type></span><span class="sxs-lookup"><span data-stu-id="c1f40-229">\<type></span></span>|<span data-ttu-id="c1f40-230">指定在組件中找到的型別，以用於產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="c1f40-230">Specifies a type found in an assembly to generate a schema for.</span></span>|
|<span data-ttu-id="c1f40-231">\<xml></span><span class="sxs-lookup"><span data-stu-id="c1f40-231">\<xml></span></span>|<span data-ttu-id="c1f40-232">指定用於產生結構描述的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="c1f40-232">Specifies an XML file to generate a schema for.</span></span>|
|<span data-ttu-id="c1f40-233">\<xdr ></span><span class="sxs-lookup"><span data-stu-id="c1f40-233">\<xdr></span></span>|<span data-ttu-id="c1f40-234">指定用於產生結構描述的 XDR 檔案。</span><span class="sxs-lookup"><span data-stu-id="c1f40-234">Specifies an XDR file to generate a schema for.</span></span>|

<span data-ttu-id="c1f40-235">若要產生程式碼檔，請使用 `<generateClasses>` 項目。</span><span class="sxs-lookup"><span data-stu-id="c1f40-235">To generate a code file, use the `<generateClasses>` element.</span></span> <span data-ttu-id="c1f40-236">下列範例會產生程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="c1f40-236">The following example generates a code file.</span></span> <span data-ttu-id="c1f40-237">請注意，也會顯示兩個屬性，可讓您設定所產生檔案的程式設計語言和命名空間。</span><span class="sxs-lookup"><span data-stu-id="c1f40-237">Note that two attributes are also shown that allow you to set the programming language and namespace of the generated file.</span></span>

```xml
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
<generateClasses language='VB' namespace='Microsoft.Serialization.Examples'/>
</xsd>
<!-- You must supply an .xsd file when typing in the command line.-->
<!-- For example: xsd /p:genClasses mySchema.xsd -->
```

 <span data-ttu-id="c1f40-238">您可以對 `<generateClasses>` 項目設定的選項包括下列各項。</span><span class="sxs-lookup"><span data-stu-id="c1f40-238">Options you can set for the `<generateClasses>` element include the following.</span></span>

|<span data-ttu-id="c1f40-239">元素</span><span class="sxs-lookup"><span data-stu-id="c1f40-239">Element</span></span>|<span data-ttu-id="c1f40-240">描述</span><span class="sxs-lookup"><span data-stu-id="c1f40-240">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="c1f40-241">\<element></span><span class="sxs-lookup"><span data-stu-id="c1f40-241">\<element></span></span>|<span data-ttu-id="c1f40-242">指定要產生程式碼之 .xsd 檔案中的項目。</span><span class="sxs-lookup"><span data-stu-id="c1f40-242">Specifies an element in the .xsd file to generate code for.</span></span>|
|<span data-ttu-id="c1f40-243">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="c1f40-243">\<schemaImporterExtensions></span></span>|<span data-ttu-id="c1f40-244">指定衍生自 <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> 類別的型別。</span><span class="sxs-lookup"><span data-stu-id="c1f40-244">Specifies a type derived from the <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> class.</span></span>|
|<span data-ttu-id="c1f40-245">\<schema></span><span class="sxs-lookup"><span data-stu-id="c1f40-245">\<schema></span></span>|<span data-ttu-id="c1f40-246">指定用於產生程式碼的 XML 結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="c1f40-246">Specifies a XML Schema file to generate code for.</span></span> <span data-ttu-id="c1f40-247">多個 XML 結構描述檔案可以使用多個 \<schema> 元素指定。</span><span class="sxs-lookup"><span data-stu-id="c1f40-247">Multiple XML Schema files can be specified using multiple \<schema> elements.</span></span>|

<span data-ttu-id="c1f40-248">下表顯示也可以和 `<generateClasses>` 項目搭配使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="c1f40-248">The following table shows the attributes that can also be used with the `<generateClasses>` element.</span></span>

|<span data-ttu-id="c1f40-249">屬性</span><span class="sxs-lookup"><span data-stu-id="c1f40-249">Attribute</span></span>|<span data-ttu-id="c1f40-250">描述</span><span class="sxs-lookup"><span data-stu-id="c1f40-250">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="c1f40-251">語言</span><span class="sxs-lookup"><span data-stu-id="c1f40-251">language</span></span>|<span data-ttu-id="c1f40-252">指定要使用的程式語言。</span><span class="sxs-lookup"><span data-stu-id="c1f40-252">Specifies the programming language to use.</span></span> <span data-ttu-id="c1f40-253">可以選擇 `CS` (C#，此為預設值)、`VB` (Visual Basic)、`JS` (JScript) 或 `VJS` (Visual J#)。</span><span class="sxs-lookup"><span data-stu-id="c1f40-253">Choose from `CS` (C#, the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="c1f40-254">您可以對實作 <xref:System.CodeDom.Compiler.CodeDomProvider> 的類別指定完整名稱。</span><span class="sxs-lookup"><span data-stu-id="c1f40-254">You can also specify a fully qualified name for a class that implements <xref:System.CodeDom.Compiler.CodeDomProvider>.</span></span>|
|<span data-ttu-id="c1f40-255">namespace</span><span class="sxs-lookup"><span data-stu-id="c1f40-255">namespace</span></span>|<span data-ttu-id="c1f40-256">指定產生之程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="c1f40-256">Specifies the namespace for the generated code.</span></span> <span data-ttu-id="c1f40-257">命名空間必須符合 CLR 標準 (例如，沒有空白或反斜線字元)。</span><span class="sxs-lookup"><span data-stu-id="c1f40-257">The namespace must conform to CLR standards (for example, no spaces or backslash characters).</span></span>|
|<span data-ttu-id="c1f40-258">選項</span><span class="sxs-lookup"><span data-stu-id="c1f40-258">options</span></span>|<span data-ttu-id="c1f40-259">下列其中一個值：`none`、`properties` (產生屬性而非公用欄位)、`order` 或 `enableDataBinding` (請參閱先前＜XSD 檔案選項＞一節中的 `/order` 和 `/enableDataBinding` 參數)。</span><span class="sxs-lookup"><span data-stu-id="c1f40-259">One of the following values: `none`, `properties` (generates properties instead of public fields), `order`, or `enableDataBinding` (see the `/order` and `/enableDataBinding` switches in the preceding XSD File Options section.</span></span>|

 <span data-ttu-id="c1f40-260">您也可以使用 `DataSet` 項目，控制產生 `<generateDataSet>` 程式碼的方法。</span><span class="sxs-lookup"><span data-stu-id="c1f40-260">You can also control how `DataSet` code is generated by using the `<generateDataSet>` element.</span></span> <span data-ttu-id="c1f40-261">下列 XML 會指定產生的程式碼使用`DataSet`結構（例如<xref:System.Data.DataTable>類別）來建立所指定專案的 Visual Basic 程式碼。</span><span class="sxs-lookup"><span data-stu-id="c1f40-261">The following XML specifies that the generated code uses `DataSet` structures (such as the <xref:System.Data.DataTable> class) to create Visual Basic code for a specified element.</span></span> <span data-ttu-id="c1f40-262">所產生的 DataSet 結構將會支援 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="c1f40-262">The generated DataSet structures will support LINQ queries.</span></span>

 ```xml
 <xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>
     <generateDataSet language='VB' namespace='Microsoft.Serialization.Examples' enableLinqDataSet='true'>
     </generateDataSet>
 </xsd>
```

<span data-ttu-id="c1f40-263">您可以對 `<generateDataSet>` 項目設定的選項包括下列各項。</span><span class="sxs-lookup"><span data-stu-id="c1f40-263">Options you can set for the `<generateDataSet>` element include the following.</span></span>

|<span data-ttu-id="c1f40-264">元素</span><span class="sxs-lookup"><span data-stu-id="c1f40-264">Element</span></span>|<span data-ttu-id="c1f40-265">描述</span><span class="sxs-lookup"><span data-stu-id="c1f40-265">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="c1f40-266">\<schema></span><span class="sxs-lookup"><span data-stu-id="c1f40-266">\<schema></span></span>|<span data-ttu-id="c1f40-267">指定用於產生程式碼的 XML 結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="c1f40-267">Specifies an XML Schema file to generate code for.</span></span> <span data-ttu-id="c1f40-268">多個 XML 結構描述檔案可以使用多個 \<schema> 元素指定。</span><span class="sxs-lookup"><span data-stu-id="c1f40-268">Multiple XML Schema files can be specified using multiple \<schema> elements.</span></span>|

 <span data-ttu-id="c1f40-269">下表顯示可以和 `<generateDataSet>` 項目搭配使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="c1f40-269">The following table shows the attributes that can be used with the `<generateDataSet>` element.</span></span>

|<span data-ttu-id="c1f40-270">屬性</span><span class="sxs-lookup"><span data-stu-id="c1f40-270">Attribute</span></span>|<span data-ttu-id="c1f40-271">說明</span><span class="sxs-lookup"><span data-stu-id="c1f40-271">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="c1f40-272">enableLinqDataSet</span><span class="sxs-lookup"><span data-stu-id="c1f40-272">enableLinqDataSet</span></span>|<span data-ttu-id="c1f40-273">指定產生的 DataSet 可使用 LINQ to DataSet 查詢。</span><span class="sxs-lookup"><span data-stu-id="c1f40-273">Specifies that the generated DataSet can be queried against using LINQ to DataSet.</span></span> <span data-ttu-id="c1f40-274">預設值為 false。</span><span class="sxs-lookup"><span data-stu-id="c1f40-274">The default value is false.</span></span>|
|<span data-ttu-id="c1f40-275">語言</span><span class="sxs-lookup"><span data-stu-id="c1f40-275">language</span></span>|<span data-ttu-id="c1f40-276">指定要使用的程式語言。</span><span class="sxs-lookup"><span data-stu-id="c1f40-276">Specifies the programming language to use.</span></span> <span data-ttu-id="c1f40-277">可以選擇 `CS` (C#，此為預設值)、`VB` (Visual Basic)、`JS` (JScript) 或 `VJS` (Visual J#)。</span><span class="sxs-lookup"><span data-stu-id="c1f40-277">Choose from `CS` (C#, the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="c1f40-278">您可以對實作 <xref:System.CodeDom.Compiler.CodeDomProvider> 的類別指定完整名稱。</span><span class="sxs-lookup"><span data-stu-id="c1f40-278">You can also specify a fully qualified name for a class that implements <xref:System.CodeDom.Compiler.CodeDomProvider>.</span></span>|
|<span data-ttu-id="c1f40-279">namespace</span><span class="sxs-lookup"><span data-stu-id="c1f40-279">namespace</span></span>|<span data-ttu-id="c1f40-280">指定產生之程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="c1f40-280">Specifies the namespace for the generated code.</span></span> <span data-ttu-id="c1f40-281">命名空間必須符合 CLR 標準 (例如，沒有空白或反斜線字元)。</span><span class="sxs-lookup"><span data-stu-id="c1f40-281">The namespace must conform to CLR standards (for example, no spaces or backslash characters).</span></span>|

 <span data-ttu-id="c1f40-282">在最上層 `<xsd>` 項目中有一些您可以設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="c1f40-282">There are attributes that you can set on the top level `<xsd>` element.</span></span> <span data-ttu-id="c1f40-283">這些選項可以和任何子項目搭配使用 (`<generateSchemas>`、`<generateClasses>` 或 `<generateDataSet>`)。</span><span class="sxs-lookup"><span data-stu-id="c1f40-283">These options can be used with any of the child elements (`<generateSchemas>`, `<generateClasses>` or `<generateDataSet>`).</span></span> <span data-ttu-id="c1f40-284">下列 XML 程式碼會對名為 "IDItems" 的項目，在名為 "MyOutputDirectory" 的輸出目錄中產生程式碼。</span><span class="sxs-lookup"><span data-stu-id="c1f40-284">The following XML code generates code for an element named "IDItems" in the output directory named "MyOutputDirectory".</span></span>

```xml
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/' output='MyOutputDirectory'>
<generateClasses>
    <element>IDItems</element>
</generateClasses>
</xsd>
```

<span data-ttu-id="c1f40-285">下表顯示也可以和 `<xsd>` 項目搭配使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="c1f40-285">The following table shows the attributes that can also be used with the `<xsd>` element.</span></span>

|<span data-ttu-id="c1f40-286">屬性</span><span class="sxs-lookup"><span data-stu-id="c1f40-286">Attribute</span></span>|<span data-ttu-id="c1f40-287">說明</span><span class="sxs-lookup"><span data-stu-id="c1f40-287">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="c1f40-288">output</span><span class="sxs-lookup"><span data-stu-id="c1f40-288">output</span></span>|<span data-ttu-id="c1f40-289">將放置產生的結構描述或程式碼檔的目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="c1f40-289">The name of a directory where the generated schema or code file will be placed.</span></span>|
|<span data-ttu-id="c1f40-290">nologo</span><span class="sxs-lookup"><span data-stu-id="c1f40-290">nologo</span></span>|<span data-ttu-id="c1f40-291">隱藏產品啟始畫面。</span><span class="sxs-lookup"><span data-stu-id="c1f40-291">Suppresses the banner.</span></span> <span data-ttu-id="c1f40-292">設為 `true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="c1f40-292">Set to `true` or `false`.</span></span>|
|<span data-ttu-id="c1f40-293">help</span><span class="sxs-lookup"><span data-stu-id="c1f40-293">help</span></span>|<span data-ttu-id="c1f40-294">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="c1f40-294">Displays command syntax and options for the tool.</span></span> <span data-ttu-id="c1f40-295">設為 `true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="c1f40-295">Set to `true` or `false`.</span></span>|

## <a name="examples"></a><span data-ttu-id="c1f40-296">範例</span><span class="sxs-lookup"><span data-stu-id="c1f40-296">Examples</span></span>
 <span data-ttu-id="c1f40-297">下列命令會從 `myFile.xdr` 產生 XML 結構描述，並將它儲存到目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="c1f40-297">The following command generates an XML schema from `myFile.xdr` and saves it to the current directory.</span></span>

```console
xsd myFile.xdr
```

<span data-ttu-id="c1f40-298">下列命令會從 `myFile.xml` 產生 XML 結構描述，並將它儲存到指定的目錄。</span><span class="sxs-lookup"><span data-stu-id="c1f40-298">The following command generates an XML schema from `myFile.xml` and saves it to the specified directory.</span></span>

```console
xsd myFile.xml /outputdir:myOutputDir
```

<span data-ttu-id="c1f40-299">下列命令會產生對應到以 C# 語言指定之結構描述的資料集，並在目前的目錄中將它儲存為 `XSDSchemaFile.cs`。</span><span class="sxs-lookup"><span data-stu-id="c1f40-299">The following command generates a data set that corresponds to the specified schema in the C# language and saves it as `XSDSchemaFile.cs` in the current directory.</span></span>

```console
xsd /dataset /language:CS XSDSchemaFile.xsd
```

<span data-ttu-id="c1f40-300">下列命令會對 `myAssembly.dll` 組件中的所有型別產生 XML 結構描述，並在目前的目錄中將它們儲存為 `schema0.xsd`。</span><span class="sxs-lookup"><span data-stu-id="c1f40-300">The following command generates XML schemas for all types in the assembly `myAssembly.dll` and saves them as `schema0.xsd` in the current directory.</span></span>

```console
xsd myAssembly.dll
```

## <a name="see-also"></a><span data-ttu-id="c1f40-301">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1f40-301">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
- [<span data-ttu-id="c1f40-302">工具</span><span class="sxs-lookup"><span data-stu-id="c1f40-302">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="c1f40-303">命令提示字元</span><span class="sxs-lookup"><span data-stu-id="c1f40-303">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
- [<span data-ttu-id="c1f40-304">LINQ to DataSet 概觀</span><span class="sxs-lookup"><span data-stu-id="c1f40-304">LINQ to DataSet Overview</span></span>](../../../docs/framework/data/adonet/linq-to-dataset-overview.md)
- [<span data-ttu-id="c1f40-305">查詢具類型資料集</span><span class="sxs-lookup"><span data-stu-id="c1f40-305">Querying Typed DataSets</span></span>](../../../docs/framework/data/adonet/querying-typed-datasets.md)
- [<span data-ttu-id="c1f40-306">LINQ （語言整合式查詢）（c #）</span><span class="sxs-lookup"><span data-stu-id="c1f40-306">LINQ (Language-Integrated Query) (C#)</span></span>](../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="c1f40-307">LINQ （語言整合式查詢）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="c1f40-307">LINQ (Language-Integrated Query) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/index.md)
