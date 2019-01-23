---
title: XML Schema Definition Tool (Xsd.exe)
ms.date: 03/30/2017
ms.assetid: a6e6e65c-347f-4494-9457-653bf29baac2
ms.openlocfilehash: c7a2cdd9fe0be020584ab87216a9d1322be185f6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606805"
---
# <a name="xml-schema-definition-tool-xsdexe"></a><span data-ttu-id="7c11e-102">XML Schema Definition Tool (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="7c11e-102">XML Schema Definition Tool (Xsd.exe)</span></span>
<span data-ttu-id="7c11e-103">XML 結構描述定義工具 (Xsd.exe) 可以從 XDR、XML 和 XSD 檔案或從執行階段組件的類別中，產生 XML 結構描述或 Common Language Runtime 類別。</span><span class="sxs-lookup"><span data-stu-id="7c11e-103">The XML Schema Definition (Xsd.exe) tool generates XML schema or common language runtime classes from XDR, XML, and XSD files, or from classes in a runtime assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c11e-104">語法</span><span class="sxs-lookup"><span data-stu-id="7c11e-104">Syntax</span></span>  
  
```  
xsd file.xdr [/outputdir:directory][/parameters:file.xml]  
xsd file.xml [/outputdir:directory] [/parameters:file.xml]  
xsd file.xsd {/classes | /dataset} [/element:element]   
             [/enableLinqDataSet] [/language:language]   
                          [/namespace:namespace] [/outputdir:directory] [URI:uri]   
                          [/parameters:file.xml]  
xsd {file.dll | file.exe} [/outputdir:directory] [/type:typename [...]][/parameters:file.xml]  
```  
  
## <a name="argument"></a><span data-ttu-id="7c11e-105">引數</span><span class="sxs-lookup"><span data-stu-id="7c11e-105">Argument</span></span>  
  
|<span data-ttu-id="7c11e-106">引數</span><span class="sxs-lookup"><span data-stu-id="7c11e-106">Argument</span></span>|<span data-ttu-id="7c11e-107">描述</span><span class="sxs-lookup"><span data-stu-id="7c11e-107">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="7c11e-108">*file.extension*</span><span class="sxs-lookup"><span data-stu-id="7c11e-108">*file.extension*</span></span>|<span data-ttu-id="7c11e-109">指定要轉換的輸入檔。</span><span class="sxs-lookup"><span data-stu-id="7c11e-109">Specifies the input file to convert.</span></span> <span data-ttu-id="7c11e-110">您必須指定以下所列的副檔名：.xdr、.xml、.xsd、.dll 或 .exe。</span><span class="sxs-lookup"><span data-stu-id="7c11e-110">You must specify the extensionas one of the following: .xdr, .xml, .xsd, .dll, or .exe.</span></span><br /><br /> <span data-ttu-id="7c11e-111">如果指定 XDR 結構描述檔 (副檔名為 .xdr )，Xsd.exe 會將 XDR 結構描述轉換成 XSD 結構描述。</span><span class="sxs-lookup"><span data-stu-id="7c11e-111">If you specify an XDR schema file (.xdr extension), Xsd.exe converts the XDR schema to an XSD schema.</span></span> <span data-ttu-id="7c11e-112">輸出檔有和 XDR 結構描述一樣的名稱，但是具有 .xsd 副檔名。</span><span class="sxs-lookup"><span data-stu-id="7c11e-112">The output file has the same name as the XDR schema, but with the .xsd extension.</span></span><br /><br /> <span data-ttu-id="7c11e-113">如果指定 XML 檔 (副檔名為 .xml )，Xsd.exe 會從檔案中的資料推斷結構描述，然後產生 XSD 結構描述。</span><span class="sxs-lookup"><span data-stu-id="7c11e-113">If you specify an XML file (.xml extension), Xsd.exe infers a schema from the data in the file and produces an XSD schema.</span></span> <span data-ttu-id="7c11e-114">輸出檔有和 XML 檔一樣的名稱，但是具有 .xsd 副檔名。</span><span class="sxs-lookup"><span data-stu-id="7c11e-114">The output file has the same name as the XML file, but with the .xsd extension.</span></span><br /><br /> <span data-ttu-id="7c11e-115">如果指定 XML 結構描述檔 (.xsd 副檔名)，Xsd.exe 會產生對應到 XML 結構描述之 Runtime 物件的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="7c11e-115">If you specify an XML schema file (.xsd extension), Xsd.exe generates source code for runtime objects that correspond to the XML schema.</span></span><br /><br /> <span data-ttu-id="7c11e-116">如果指定執行階段組件檔 (.exe 或 .dll 副檔名)，Xsd.exe 會產生該組件中一個或多個型別的結構描述。</span><span class="sxs-lookup"><span data-stu-id="7c11e-116">If you specify a runtime assembly file (.exe or .dll extension), Xsd.exe generates schemas for one or more types in that assembly.</span></span> <span data-ttu-id="7c11e-117">您可以使用 `/type` 選項來指定要產生結構描述的型別。</span><span class="sxs-lookup"><span data-stu-id="7c11e-117">You can use the `/type` option to specify the types for which to generate schemas.</span></span> <span data-ttu-id="7c11e-118">輸出結構描述被命名為 schema0.xsd、schema1.xsd 等等。</span><span class="sxs-lookup"><span data-stu-id="7c11e-118">The output schemas are named schema0.xsd, schema1.xsd, and so on.</span></span> <span data-ttu-id="7c11e-119">只有在指定的型別使用 `XMLRoot` 自訂屬性來指定命名空間 (Namespace) 時，Xsd.exe 才能產生多個結構描述。</span><span class="sxs-lookup"><span data-stu-id="7c11e-119">Xsd.exe produces multiple schemas only if the given types specify a namespace using the `XMLRoot` custom attribute.</span></span>|  
  
## <a name="general-options"></a><span data-ttu-id="7c11e-120">一般選項</span><span class="sxs-lookup"><span data-stu-id="7c11e-120">General Options</span></span>  
  
|<span data-ttu-id="7c11e-121">選項</span><span class="sxs-lookup"><span data-stu-id="7c11e-121">Option</span></span>|<span data-ttu-id="7c11e-122">描述</span><span class="sxs-lookup"><span data-stu-id="7c11e-122">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="7c11e-123">**/h\[elp\]**</span><span class="sxs-lookup"><span data-stu-id="7c11e-123">**/h\[elp\]**</span></span>|<span data-ttu-id="7c11e-124">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="7c11e-124">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="7c11e-125">**/o\[utputdir\]:**_directory_</span><span class="sxs-lookup"><span data-stu-id="7c11e-125">**/o\[utputdir\]:**_directory_</span></span>|<span data-ttu-id="7c11e-126">指定輸出檔的目錄。</span><span class="sxs-lookup"><span data-stu-id="7c11e-126">Specifies the directory for output files.</span></span> <span data-ttu-id="7c11e-127">這個引數只可以使用一次。</span><span class="sxs-lookup"><span data-stu-id="7c11e-127">This argument can appear only once.</span></span> <span data-ttu-id="7c11e-128">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="7c11e-128">The default is the current directory.</span></span>|  
|<span data-ttu-id="7c11e-129">**/?**</span><span class="sxs-lookup"><span data-stu-id="7c11e-129">**/?**</span></span>|<span data-ttu-id="7c11e-130">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="7c11e-130">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="7c11e-131">**/p\[arameters\]:**_file.xml_</span><span class="sxs-lookup"><span data-stu-id="7c11e-131">**/p\[arameters\]:**_file.xml_</span></span>|<span data-ttu-id="7c11e-132">從指定的 .xml 檔案，讀取各種作業模式的選項。</span><span class="sxs-lookup"><span data-stu-id="7c11e-132">Read options for various operation modes from the specified .xml file.</span></span> <span data-ttu-id="7c11e-133">簡短形式為 `/p:`。</span><span class="sxs-lookup"><span data-stu-id="7c11e-133">The short form is `/p:`.</span></span> <span data-ttu-id="7c11e-134">如需詳細資訊，請參閱 <<c0> [ 備註](#remarks)一節。</span><span class="sxs-lookup"><span data-stu-id="7c11e-134">For more information, see the [Remarks](#remarks) section.</span></span>|  
  
## <a name="xsd-file-options"></a><span data-ttu-id="7c11e-135">XSD 檔案選項</span><span class="sxs-lookup"><span data-stu-id="7c11e-135">XSD File Options</span></span>  
 <span data-ttu-id="7c11e-136">您只能為 .xsd 檔指定下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="7c11e-136">You must specify only one of the following options for .xsd files.</span></span>  
  
|<span data-ttu-id="7c11e-137">選項</span><span class="sxs-lookup"><span data-stu-id="7c11e-137">Option</span></span>|<span data-ttu-id="7c11e-138">描述</span><span class="sxs-lookup"><span data-stu-id="7c11e-138">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="7c11e-139">**/c\[lasses\]**</span><span class="sxs-lookup"><span data-stu-id="7c11e-139">**/c\[lasses\]**</span></span>|<span data-ttu-id="7c11e-140">產生對應到指定的結構描述的類別。</span><span class="sxs-lookup"><span data-stu-id="7c11e-140">Generates classes that correspond to the specified schema.</span></span> <span data-ttu-id="7c11e-141">若要將 XML 資料讀入物件，請使用 <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="7c11e-141">To read XML data into the object, use the <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="7c11e-142">**/d[ataset]**</span><span class="sxs-lookup"><span data-stu-id="7c11e-142">**/d[ataset]**</span></span>|<span data-ttu-id="7c11e-143">產生衍生自 <xref:System.Data.DataSet> 的類別，對應到指定的結構描述。</span><span class="sxs-lookup"><span data-stu-id="7c11e-143">Generates a class derived from <xref:System.Data.DataSet> that corresponds to the specified schema.</span></span> <span data-ttu-id="7c11e-144">若要將 XML 資料讀入衍生類別，請使用 <xref:System.Data.DataSet.ReadXml%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="7c11e-144">To read XML data into the derived class, use the <xref:System.Data.DataSet.ReadXml%2A?displayProperty=nameWithType> method.</span></span>|  
  
 <span data-ttu-id="7c11e-145">您也可以為 .xsd 檔指定下列任何選項：</span><span class="sxs-lookup"><span data-stu-id="7c11e-145">You can also specify any of the following options for .xsd files.</span></span>  
  
|<span data-ttu-id="7c11e-146">選項</span><span class="sxs-lookup"><span data-stu-id="7c11e-146">Option</span></span>|<span data-ttu-id="7c11e-147">描述</span><span class="sxs-lookup"><span data-stu-id="7c11e-147">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="7c11e-148">**/e\[lement\]:**_element_</span><span class="sxs-lookup"><span data-stu-id="7c11e-148">**/e\[lement\]:**_element_</span></span>|<span data-ttu-id="7c11e-149">指定所要產生程式碼的結構描述中的項目。</span><span class="sxs-lookup"><span data-stu-id="7c11e-149">Specifies the element in the schema to generate code for.</span></span> <span data-ttu-id="7c11e-150">根據預設，會輸入所有項目。</span><span class="sxs-lookup"><span data-stu-id="7c11e-150">By default all elements are typed.</span></span> <span data-ttu-id="7c11e-151">您可以多次指定這個引數。</span><span class="sxs-lookup"><span data-stu-id="7c11e-151">You can specify this argument more than once.</span></span>|  
|<span data-ttu-id="7c11e-152">**/enableDataBinding**</span><span class="sxs-lookup"><span data-stu-id="7c11e-152">**/enableDataBinding**</span></span>|<span data-ttu-id="7c11e-153">在所有產生的型別上實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面，以啟用資料繫結 (Data Binding)。</span><span class="sxs-lookup"><span data-stu-id="7c11e-153">Implements the <xref:System.ComponentModel.INotifyPropertyChanged> interface on all generated types to enable data binding.</span></span> <span data-ttu-id="7c11e-154">簡短形式為 `/edb`。</span><span class="sxs-lookup"><span data-stu-id="7c11e-154">The short form is `/edb`.</span></span>|  
|<span data-ttu-id="7c11e-155">**/enableLinqDataSet**</span><span class="sxs-lookup"><span data-stu-id="7c11e-155">**/enableLinqDataSet**</span></span>|<span data-ttu-id="7c11e-156">(簡短形式：`/eld`)。指定產生的 DataSet 可使用 LINQ to DataSet 查詢。</span><span class="sxs-lookup"><span data-stu-id="7c11e-156">(Short form: `/eld`.) Specifies that the generated DataSet can be queried against using LINQ to DataSet.</span></span> <span data-ttu-id="7c11e-157">如果也指定了 /dataset 選項，就會使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="7c11e-157">This option is used when the /dataset option is also specified.</span></span> <span data-ttu-id="7c11e-158">如需詳細資訊，請參閱 [LINQ to DataSet 概觀](../../../docs/framework/data/adonet/linq-to-dataset-overview.md)和[查詢具類型資料集](../../../docs/framework/data/adonet/querying-typed-datasets.md)。</span><span class="sxs-lookup"><span data-stu-id="7c11e-158">For more information, see [LINQ to DataSet Overview](../../../docs/framework/data/adonet/linq-to-dataset-overview.md) and [Querying Typed DataSets](../../../docs/framework/data/adonet/querying-typed-datasets.md).</span></span> <span data-ttu-id="7c11e-159">如需使用 LINQ 的一般資訊，請參閱 [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)。</span><span class="sxs-lookup"><span data-stu-id="7c11e-159">For general information about using LINQ, see [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).</span></span>|  
|<span data-ttu-id="7c11e-160">**/f\[ields\]**</span><span class="sxs-lookup"><span data-stu-id="7c11e-160">**/f\[ields\]**</span></span>|<span data-ttu-id="7c11e-161">產生欄位，而不是產生屬性。</span><span class="sxs-lookup"><span data-stu-id="7c11e-161">Generates fields instead of properties.</span></span> <span data-ttu-id="7c11e-162">根據預設，會產生屬性。</span><span class="sxs-lookup"><span data-stu-id="7c11e-162">By default, properties are generated.</span></span>|  
|<span data-ttu-id="7c11e-163">**/l\[anguage\]:**_language_</span><span class="sxs-lookup"><span data-stu-id="7c11e-163">**/l\[anguage\]:**_language_</span></span>|<span data-ttu-id="7c11e-164">指定要使用的程式語言。</span><span class="sxs-lookup"><span data-stu-id="7c11e-164">Specifies the programming language to use.</span></span> <span data-ttu-id="7c11e-165">可以選擇 `CS` (C#，此為預設值)、`VB` (Visual Basic)、`JS` (JScript) 或 `VJS` (Visual J#)。</span><span class="sxs-lookup"><span data-stu-id="7c11e-165">Choose from `CS` (C#, which is the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="7c11e-166">您也可以對實作 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> 的類別指定完整名稱。</span><span class="sxs-lookup"><span data-stu-id="7c11e-166">You can also specify a fully qualified name for a class implementing <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType></span></span>|  
|<span data-ttu-id="7c11e-167">**/n\[amespace\]:**_namespace_</span><span class="sxs-lookup"><span data-stu-id="7c11e-167">**/n\[amespace\]:**_namespace_</span></span>|<span data-ttu-id="7c11e-168">指定產生的型別的執行階段命名空間。</span><span class="sxs-lookup"><span data-stu-id="7c11e-168">Specifies the runtime namespace for the generated types.</span></span> <span data-ttu-id="7c11e-169">預設命名空間是 `Schemas`。</span><span class="sxs-lookup"><span data-stu-id="7c11e-169">The default namespace is `Schemas`.</span></span>|  
|<span data-ttu-id="7c11e-170">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="7c11e-170">**/nologo**</span></span>|<span data-ttu-id="7c11e-171">隱藏產品啟始畫面。</span><span class="sxs-lookup"><span data-stu-id="7c11e-171">Suppresses the banner.</span></span>|  
|<span data-ttu-id="7c11e-172">**/order**</span><span class="sxs-lookup"><span data-stu-id="7c11e-172">**/order**</span></span>|<span data-ttu-id="7c11e-173">在所有物件成員上產生明確順序識別項。</span><span class="sxs-lookup"><span data-stu-id="7c11e-173">Generates explicit order identifiers on all particle members.</span></span>|  
|<span data-ttu-id="7c11e-174">**/o\[ut\]:**_directoryName_</span><span class="sxs-lookup"><span data-stu-id="7c11e-174">**/o\[ut\]:**_directoryName_</span></span>|<span data-ttu-id="7c11e-175">指定要在其中放置檔案的輸出目錄。</span><span class="sxs-lookup"><span data-stu-id="7c11e-175">Specifies the output directory to place the files in.</span></span> <span data-ttu-id="7c11e-176">預設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="7c11e-176">The default is the current directory.</span></span>|  
|<span data-ttu-id="7c11e-177">**/u\[ri\]:**_uri_</span><span class="sxs-lookup"><span data-stu-id="7c11e-177">**/u\[ri\]:**_uri_</span></span>|<span data-ttu-id="7c11e-178">指定所要產生程式碼的結構描述中項目的 URI。</span><span class="sxs-lookup"><span data-stu-id="7c11e-178">Specifies the URI for the elements in the schema to generate code for.</span></span> <span data-ttu-id="7c11e-179">這個 URI 如果存在，會套用到所有以 `/element` 選項指定的項目。</span><span class="sxs-lookup"><span data-stu-id="7c11e-179">This URI, if present, applies to all elements specified with the `/element` option.</span></span>|  
  
## <a name="dll-and-exe-file-options"></a><span data-ttu-id="7c11e-180">DLL 和 EXE 檔案選項</span><span class="sxs-lookup"><span data-stu-id="7c11e-180">DLL and EXE File Options</span></span>  
  
|<span data-ttu-id="7c11e-181">選項</span><span class="sxs-lookup"><span data-stu-id="7c11e-181">Option</span></span>|<span data-ttu-id="7c11e-182">描述</span><span class="sxs-lookup"><span data-stu-id="7c11e-182">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="7c11e-183">**/t\[ype\]:**_typename_</span><span class="sxs-lookup"><span data-stu-id="7c11e-183">**/t\[ype\]:**_typename_</span></span>|<span data-ttu-id="7c11e-184">指定所要建立結構描述的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="7c11e-184">Specifies the name of the type to create a schema for.</span></span> <span data-ttu-id="7c11e-185">您可以指定多個型別引數。</span><span class="sxs-lookup"><span data-stu-id="7c11e-185">You can specify multiple type arguments.</span></span> <span data-ttu-id="7c11e-186">如果 *typename* 沒有指定命名空間，Xsd.exe 會以指定的類型比對組件中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="7c11e-186">If *typename* does not specify a namespace, Xsd.exe matches all types in the assembly with the specified type.</span></span> <span data-ttu-id="7c11e-187">如果 *typename* 指定命名空間，只有該類型會被比對。</span><span class="sxs-lookup"><span data-stu-id="7c11e-187">If *typename* specifies a namespace, only that type is matched.</span></span> <span data-ttu-id="7c11e-188">如果 *typename* 結尾為星號字元 (\*)，則工具會比對 \* 之前以這個字串為開頭的所有類型。</span><span class="sxs-lookup"><span data-stu-id="7c11e-188">If *typename* ends with an asterisk character (\*), the tool matches all types that start with the string preceding the \*.</span></span> <span data-ttu-id="7c11e-189">如果省略 `/type` 選項，Xsd.exe 會產生組件中所有型別的結構描述。</span><span class="sxs-lookup"><span data-stu-id="7c11e-189">If you omit the `/type` option, Xsd.exe generates schemas for all types in the assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c11e-190">備註</span><span class="sxs-lookup"><span data-stu-id="7c11e-190">Remarks</span></span>  
 <span data-ttu-id="7c11e-191">下表列出 Xsd.exe 執行的作業。</span><span class="sxs-lookup"><span data-stu-id="7c11e-191">The following table shows the operations that Xsd.exe performs.</span></span>  

| | |  
|------------|-----------------|  
|<span data-ttu-id="7c11e-192">XDR 轉換成 XSD</span><span class="sxs-lookup"><span data-stu-id="7c11e-192">XDR to XSD</span></span>|<span data-ttu-id="7c11e-193">從 XML-Data-Reduced 結構描述檔中產生 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="7c11e-193">Generates an XML schema from an XML-Data-Reduced schema file.</span></span> <span data-ttu-id="7c11e-194">XDR 是早期 XML 架構的結構描述。</span><span class="sxs-lookup"><span data-stu-id="7c11e-194">XDR is an early XML-based schema format.</span></span>| 
|<span data-ttu-id="7c11e-195">XML 轉換成 XSD</span><span class="sxs-lookup"><span data-stu-id="7c11e-195">XML to XSD</span></span>|<span data-ttu-id="7c11e-196">從 XML 檔案中產生 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="7c11e-196">Generates an XML schema from an XML file.</span></span>|  
|<span data-ttu-id="7c11e-197">XSD 轉換成 DataSet</span><span class="sxs-lookup"><span data-stu-id="7c11e-197">XSD to DataSet</span></span>|<span data-ttu-id="7c11e-198">從 XSD 結構描述檔中產生 Common Language Runtime <xref:System.Data.DataSet> 類別。</span><span class="sxs-lookup"><span data-stu-id="7c11e-198">Generates common language runtime <xref:System.Data.DataSet> classes from an XSD schema file.</span></span> <span data-ttu-id="7c11e-199">產生的類別為一般 XML 資料提供了豐富的物件模型。</span><span class="sxs-lookup"><span data-stu-id="7c11e-199">The generated classes provide a rich object model for regular XML data.</span></span>| 
|<span data-ttu-id="7c11e-200">XSD 轉換成類別</span><span class="sxs-lookup"><span data-stu-id="7c11e-200">XSD to Classes</span></span>|<span data-ttu-id="7c11e-201">從 XSD 結構描述檔中產生執行階段類別。</span><span class="sxs-lookup"><span data-stu-id="7c11e-201">Generates runtime classes from an XSD schema file.</span></span> <span data-ttu-id="7c11e-202">產生的類別可以配合 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> 使用，以讀取和寫入遵循結構描述的 XML 程式碼。</span><span class="sxs-lookup"><span data-stu-id="7c11e-202">The generated classes can be used in conjunction with <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> to read and write XML code that follows the schema.</span></span>| 
|<span data-ttu-id="7c11e-203">類別轉換成 XSD</span><span class="sxs-lookup"><span data-stu-id="7c11e-203">Classes to XSD</span></span>| <span data-ttu-id="7c11e-204">從型別或執行階段組件檔中的型別中產生 XML 結構描述。</span><span class="sxs-lookup"><span data-stu-id="7c11e-204">Generates an XML schema from a type or types in a runtime assembly file.</span></span> <span data-ttu-id="7c11e-205">產生的結構描述會定義所使用的 XML 格式<xref:System.Xml.Serialization.XmlSerializer>。</span><span class="sxs-lookup"><span data-stu-id="7c11e-205">The generated schema defines the XML format used by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>|  
 
 <span data-ttu-id="7c11e-206">Xsd.exe 只允許您操作遵循 XML 結構描述定義 (XSD) 語言的 XML 結構描述，而這個 XSD 語言是由全球資訊網協會 (W3C) 所提出的。</span><span class="sxs-lookup"><span data-stu-id="7c11e-206">Xsd.exe only allows you to manipulate XML schemas that follow the XML Schema Definition (XSD) language proposed by the World Wide Web Consortium (W3C).</span></span> <span data-ttu-id="7c11e-207">如需有關 XML 結構描述定義提議或 XML 標準的詳細資訊，請參閱<https://w3.org>。</span><span class="sxs-lookup"><span data-stu-id="7c11e-207">For more information on the XML Schema Definition proposal or the XML standard, see <https://w3.org>.</span></span>  
  
## <a name="setting-options-with-an-xml-file"></a><span data-ttu-id="7c11e-208">設定 XML 檔案的選項</span><span class="sxs-lookup"><span data-stu-id="7c11e-208">Setting Options with an XML File</span></span>  
 <span data-ttu-id="7c11e-209">使用 `/parameters` 參數時，您可以指定會設定各種選項的單一 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="7c11e-209">By using the `/parameters` switch, you can specify a single XML file that sets various options.</span></span> <span data-ttu-id="7c11e-210">您可以設定的選項會視使用 XSD.exe 工具的方式而定。</span><span class="sxs-lookup"><span data-stu-id="7c11e-210">The options you can set depend on how you are using the XSD.exe tool.</span></span> <span data-ttu-id="7c11e-211">這些選擇包括產生結構描述、產生程式碼檔或產生內含 `DataSet` 功能的程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="7c11e-211">Choices include generating schemas, generating code files, or generating code files that include `DataSet` features.</span></span> <span data-ttu-id="7c11e-212">例如，您可以在產生結構描述時 (但不是在產生程式碼檔案時)，將 `<assembly>` 項目設為可執行檔 (.exe) 或型別程式庫 (.dll) 檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="7c11e-212">For example, you can set the `<assembly>` element to the name of an executable (.exe) or type library (.dll) file when generating a schema, but not when generating a code file.</span></span> <span data-ttu-id="7c11e-213">下列 XML 會顯示如何使用 `<generateSchemas>` 項目搭配指定的可執行檔：</span><span class="sxs-lookup"><span data-stu-id="7c11e-213">The following XML shows how to use the `<generateSchemas>` element with a specified executable:</span></span>  
  
```xml  
<!-- This is in a file named GenerateSchemas.xml. -->  
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>  
<generateSchemas>  
   <assembly>ConsoleApplication1.exe</assembly>  
</generateSchemas>  
</xsd>  
```  
  
 <span data-ttu-id="7c11e-214">如果前一個 XML 內含在名為 GenerateSchemas.xml 的檔案中，則在命令提示字元中鍵入下列命令，並按 ENTER 鍵，就可以使用 `/parameters` 參數：</span><span class="sxs-lookup"><span data-stu-id="7c11e-214">If the preceding XML is contained in a file named GenerateSchemas.xml, then use the `/parameters` switch by typing the following at a command prompt and pressing ENTER:</span></span>  
  
```console 
 xsd /p:GenerateSchemas.xml 
```  
  
 <span data-ttu-id="7c11e-215">換句話說，如果針對在組件中找到的單一型別產生結構描述，就可以使用下列 XML：</span><span class="sxs-lookup"><span data-stu-id="7c11e-215">On the other hand, if you are generating a schema for a single type found in the assembly, you can use the following XML:</span></span>  
  
```xml  
<!-- This is in a file named GenerateSchemaFromType.xml. -->  
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>  
<generateSchemas>  
   <type>IDItems</type>  
</generateSchemas>  
</xsd>  
```  
  
 <span data-ttu-id="7c11e-216">但是若要使用之前的程式碼，您也必須在命令提示字元中提供組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="7c11e-216">But to use preceding code, you must also supply the name of the assembly at the command prompt.</span></span> <span data-ttu-id="7c11e-217">在命令提示字元中輸入下列命令 (假設 XML 檔案的名稱為 GenerateSchemaFromType.xml)：</span><span class="sxs-lookup"><span data-stu-id="7c11e-217">Type the following at a command prompt (presuming the XML file is named GenerateSchemaFromType.xml):</span></span>  
  
```console 
xsd /p:GenerateSchemaFromType.xml ConsoleApplication1.exe  
```  
 <span data-ttu-id="7c11e-218">您只能為 `\<generateSchemas>` 項目指定下列其中一個選項。</span><span class="sxs-lookup"><span data-stu-id="7c11e-218">You must specify only one of the following options for the `\<generateSchemas>` element.</span></span>  
  
|<span data-ttu-id="7c11e-219">項目</span><span class="sxs-lookup"><span data-stu-id="7c11e-219">Element</span></span>|<span data-ttu-id="7c11e-220">描述</span><span class="sxs-lookup"><span data-stu-id="7c11e-220">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7c11e-221">\<assembly></span><span class="sxs-lookup"><span data-stu-id="7c11e-221">\<assembly></span></span>|<span data-ttu-id="7c11e-222">指定要產生結構描述的組件。</span><span class="sxs-lookup"><span data-stu-id="7c11e-222">Specifies an assembly to generate the schema from.</span></span>|  
|<span data-ttu-id="7c11e-223">\<type></span><span class="sxs-lookup"><span data-stu-id="7c11e-223">\<type></span></span>|<span data-ttu-id="7c11e-224">指定在組件中找到的型別，以用於產生結構描述。</span><span class="sxs-lookup"><span data-stu-id="7c11e-224">Specifies a type found in an assembly to generate a schema for.</span></span>|  
|<span data-ttu-id="7c11e-225">\<xml></span><span class="sxs-lookup"><span data-stu-id="7c11e-225">\<xml></span></span>|<span data-ttu-id="7c11e-226">指定用於產生結構描述的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="7c11e-226">Specifies an XML file to generate a schema for.</span></span>|  
|<span data-ttu-id="7c11e-227">\<xdr ></span><span class="sxs-lookup"><span data-stu-id="7c11e-227">\<xdr></span></span>|<span data-ttu-id="7c11e-228">指定用於產生結構描述的 XDR 檔案。</span><span class="sxs-lookup"><span data-stu-id="7c11e-228">Specifies an XDR file to generate a schema for.</span></span>|  
  
 <span data-ttu-id="7c11e-229">若要產生程式碼檔，請使用 `<generateClasses>` 項目。</span><span class="sxs-lookup"><span data-stu-id="7c11e-229">To generate a code file, use the `<generateClasses>` element.</span></span> <span data-ttu-id="7c11e-230">下列範例會產生程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="7c11e-230">The following example generates a code file.</span></span> <span data-ttu-id="7c11e-231">請注意，也會顯示兩個屬性，可讓您設定所產生檔案的程式設計語言和命名空間。</span><span class="sxs-lookup"><span data-stu-id="7c11e-231">Note that two attributes are also shown that allow you to set the programming language and namespace of the generated file.</span></span>  
  
```xml  
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'>  
<generateClasses language='VB' namespace='Microsoft.Serialization.Examples'/>  
</xsd>  
<!-- You must supply an .xsd file when typing in the command line.-->  
<!-- For example: xsd /p:genClasses mySchema.xsd -->  
```  
  
 <span data-ttu-id="7c11e-232">您可以對 `\<generateClasses>` 項目設定的選項包括下列各項。</span><span class="sxs-lookup"><span data-stu-id="7c11e-232">Options you can set for the `\<generateClasses>` element include the following.</span></span>  
  
|<span data-ttu-id="7c11e-233">項目</span><span class="sxs-lookup"><span data-stu-id="7c11e-233">Element</span></span>|<span data-ttu-id="7c11e-234">描述</span><span class="sxs-lookup"><span data-stu-id="7c11e-234">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7c11e-235">\<element></span><span class="sxs-lookup"><span data-stu-id="7c11e-235">\<element></span></span>|<span data-ttu-id="7c11e-236">指定要產生程式碼之 .xsd 檔案中的項目。</span><span class="sxs-lookup"><span data-stu-id="7c11e-236">Specifies an element in the .xsd file to generate code for.</span></span>|  
|<span data-ttu-id="7c11e-237">\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="7c11e-237">\<schemaImporterExtensions></span></span>|<span data-ttu-id="7c11e-238">指定衍生自 <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> 類別的型別。</span><span class="sxs-lookup"><span data-stu-id="7c11e-238">Specifies a type derived from the <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> class.</span></span>|  
|<span data-ttu-id="7c11e-239">\<schema></span><span class="sxs-lookup"><span data-stu-id="7c11e-239">\<schema></span></span>|<span data-ttu-id="7c11e-240">指定用於產生程式碼的 XML 結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="7c11e-240">Specifies a XML Schema file to generate code for.</span></span>  <span data-ttu-id="7c11e-241">多個 XML 結構描述檔案可以使用多個 \<schema> 元素指定。</span><span class="sxs-lookup"><span data-stu-id="7c11e-241">Multiple XML Schema files can be specified using multiple \<schema> elements.</span></span>|  
  
 <span data-ttu-id="7c11e-242">下表顯示也可以和 `<generateClasses>` 項目搭配使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="7c11e-242">The following table shows the attributes that can also be used with the `<generateClasses>` element.</span></span>  
  
|<span data-ttu-id="7c11e-243">屬性</span><span class="sxs-lookup"><span data-stu-id="7c11e-243">Attribute</span></span>|<span data-ttu-id="7c11e-244">描述</span><span class="sxs-lookup"><span data-stu-id="7c11e-244">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7c11e-245">語言</span><span class="sxs-lookup"><span data-stu-id="7c11e-245">language</span></span>|<span data-ttu-id="7c11e-246">指定要使用的程式語言。</span><span class="sxs-lookup"><span data-stu-id="7c11e-246">Specifies the programming language to use.</span></span> <span data-ttu-id="7c11e-247">可以選擇 `CS` (C#，此為預設值)、`VB` (Visual Basic)、`JS` (JScript) 或 `VJS` (Visual J#)。</span><span class="sxs-lookup"><span data-stu-id="7c11e-247">Choose from `CS` (C#, the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="7c11e-248">您可以對實作 <xref:System.CodeDom.Compiler.CodeDomProvider> 的類別指定完整名稱。</span><span class="sxs-lookup"><span data-stu-id="7c11e-248">You can also specify a fully qualified name for a class that implements <xref:System.CodeDom.Compiler.CodeDomProvider>.</span></span>|  
|<span data-ttu-id="7c11e-249">namespace</span><span class="sxs-lookup"><span data-stu-id="7c11e-249">namespace</span></span>|<span data-ttu-id="7c11e-250">指定產生之程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="7c11e-250">Specifies the namespace for the generated code.</span></span> <span data-ttu-id="7c11e-251">命名空間必須符合 CLR 標準 (例如，沒有空白或反斜線字元)。</span><span class="sxs-lookup"><span data-stu-id="7c11e-251">The namespace must conform to CLR standards (for example, no spaces or backslash characters).</span></span>|  
|<span data-ttu-id="7c11e-252">選項</span><span class="sxs-lookup"><span data-stu-id="7c11e-252">options</span></span>|<span data-ttu-id="7c11e-253">下列其中一個值：`none`、`properties` (產生屬性而非公用欄位)、`order` 或 `enableDataBinding` (請參閱先前＜XSD 檔案選項＞一節中的 `/order` 和 `/enableDataBinding` 參數)。</span><span class="sxs-lookup"><span data-stu-id="7c11e-253">One of the following values: `none`, `properties` (generates properties instead of public fields), `order`, or `enableDataBinding` (see the `/order` and `/enableDataBinding` switches in the preceding XSD File Options section.</span></span>|  
  
 <span data-ttu-id="7c11e-254">您也可以使用 `DataSet` 項目，控制產生 `<generateDataSet>` 程式碼的方法。</span><span class="sxs-lookup"><span data-stu-id="7c11e-254">You can also control how `DataSet` code is generated by using the `<generateDataSet>` element.</span></span> <span data-ttu-id="7c11e-255">下列 XML 會指定產生的程式碼使用 `DataSet` 結構 (例如 <xref:System.Data.DataTable> 類別)，以建立所指定元素的 Visual Basic 程式碼。</span><span class="sxs-lookup"><span data-stu-id="7c11e-255">The following XML specifies that the generated codeuses `DataSet` structures (such as the <xref:System.Data.DataTable> class) to create Visual Basic code for a specified element.</span></span> <span data-ttu-id="7c11e-256">所產生的 DataSet 結構將會支援 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="7c11e-256">The generated DataSet structures will support LINQ queries.</span></span>  
  
 ```xml 
 <xsd xmlns='http://microsoft.com/dotnet/tools/xsd/'> 
     <generateDataSet language='VB' namespace='Microsoft.Serialization.Examples' enableLinqDataSet='true'> 
     </generateDataSet>    
 </xsd> 
``` 
 
 <span data-ttu-id="7c11e-257">您可以對 `<generateDataSet>` 項目設定的選項包括下列各項。</span><span class="sxs-lookup"><span data-stu-id="7c11e-257">Options you can set for the `<generateDataSet>` element include the following.</span></span>  
  
|<span data-ttu-id="7c11e-258">項目</span><span class="sxs-lookup"><span data-stu-id="7c11e-258">Element</span></span>|<span data-ttu-id="7c11e-259">描述</span><span class="sxs-lookup"><span data-stu-id="7c11e-259">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7c11e-260">\<schema></span><span class="sxs-lookup"><span data-stu-id="7c11e-260">\<schema></span></span>|<span data-ttu-id="7c11e-261">指定用於產生程式碼的 XML 結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="7c11e-261">Specifies an XML Schema file to generate code for.</span></span> <span data-ttu-id="7c11e-262">多個 XML 結構描述檔案可以使用多個 \<schema> 元素指定。</span><span class="sxs-lookup"><span data-stu-id="7c11e-262">Multiple XML Schema files can be specified using multiple \<schema> elements.</span></span>|  
  
 <span data-ttu-id="7c11e-263">下表顯示可以和 `<generateDataSet>` 項目搭配使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="7c11e-263">The following table shows the attributes that can be used with the `<generateDataSet>` element.</span></span>  
  
|<span data-ttu-id="7c11e-264">屬性</span><span class="sxs-lookup"><span data-stu-id="7c11e-264">Attribute</span></span>|<span data-ttu-id="7c11e-265">描述</span><span class="sxs-lookup"><span data-stu-id="7c11e-265">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7c11e-266">enableLinqDataSet</span><span class="sxs-lookup"><span data-stu-id="7c11e-266">enableLinqDataSet</span></span>|<span data-ttu-id="7c11e-267">指定產生的 DataSet 可使用 LINQ to DataSet 查詢。</span><span class="sxs-lookup"><span data-stu-id="7c11e-267">Specifies that the generated DataSet can be queried against using LINQ to DataSet.</span></span> <span data-ttu-id="7c11e-268">預設值為 false。</span><span class="sxs-lookup"><span data-stu-id="7c11e-268">The default value is false.</span></span>|  
|<span data-ttu-id="7c11e-269">語言</span><span class="sxs-lookup"><span data-stu-id="7c11e-269">language</span></span>|<span data-ttu-id="7c11e-270">指定要使用的程式語言。</span><span class="sxs-lookup"><span data-stu-id="7c11e-270">Specifies the programming language to use.</span></span> <span data-ttu-id="7c11e-271">可以選擇 `CS` (C#，此為預設值)、`VB` (Visual Basic)、`JS` (JScript) 或 `VJS` (Visual J#)。</span><span class="sxs-lookup"><span data-stu-id="7c11e-271">Choose from `CS` (C#, the default), `VB` (Visual Basic), `JS` (JScript), or `VJS` (Visual J#).</span></span> <span data-ttu-id="7c11e-272">您可以對實作 <xref:System.CodeDom.Compiler.CodeDomProvider> 的類別指定完整名稱。</span><span class="sxs-lookup"><span data-stu-id="7c11e-272">You can also specify a fully qualified name for a class that implements <xref:System.CodeDom.Compiler.CodeDomProvider>.</span></span>|  
|<span data-ttu-id="7c11e-273">namespace</span><span class="sxs-lookup"><span data-stu-id="7c11e-273">namespace</span></span>|<span data-ttu-id="7c11e-274">指定產生之程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="7c11e-274">Specifies the namespace for the generated code.</span></span> <span data-ttu-id="7c11e-275">命名空間必須符合 CLR 標準 (例如，沒有空白或反斜線字元)。</span><span class="sxs-lookup"><span data-stu-id="7c11e-275">The namespace must conform to CLR standards (for example, no spaces or backslash characters).</span></span>|  
  
 <span data-ttu-id="7c11e-276">在最上層 `<xsd>` 項目中有一些您可以設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="7c11e-276">There are attributes that you can set on the top level `<xsd>` element.</span></span> <span data-ttu-id="7c11e-277">這些選項可以和任何子項目搭配使用 (`<generateSchemas>`、`<generateClasses>` 或 `<generateDataSet>`)。</span><span class="sxs-lookup"><span data-stu-id="7c11e-277">These options can be used with any of the child elements (`<generateSchemas>`, `<generateClasses>` or `<generateDataSet>`).</span></span> <span data-ttu-id="7c11e-278">下列 XML 程式碼會對名為 "IDItems" 的項目，在名為 "MyOutputDirectory" 的輸出目錄中產生程式碼。</span><span class="sxs-lookup"><span data-stu-id="7c11e-278">The following XML code generates code for an element named "IDItems" in the output directory named "MyOutputDirectory".</span></span>  
  
```xml  
<xsd xmlns='http://microsoft.com/dotnet/tools/xsd/' output='MyOutputDirectory'>  
<generateClasses>  
    <element>IDItems</element>  
</generateClasses>  
</xsd>  
```  
  
 <span data-ttu-id="7c11e-279">下表顯示也可以和 `\<xsd>` 項目搭配使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="7c11e-279">The following table shows the attributes that can also be used with the `\<xsd>` element.</span></span>  
  
|<span data-ttu-id="7c11e-280">屬性</span><span class="sxs-lookup"><span data-stu-id="7c11e-280">Attribute</span></span>|<span data-ttu-id="7c11e-281">描述</span><span class="sxs-lookup"><span data-stu-id="7c11e-281">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7c11e-282">輸出</span><span class="sxs-lookup"><span data-stu-id="7c11e-282">output</span></span>|<span data-ttu-id="7c11e-283">將放置產生的結構描述或程式碼檔的目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="7c11e-283">The name of a directory where the generated schema or code file will be placed.</span></span>|  
|<span data-ttu-id="7c11e-284">nologo</span><span class="sxs-lookup"><span data-stu-id="7c11e-284">nologo</span></span>|<span data-ttu-id="7c11e-285">隱藏產品啟始畫面。</span><span class="sxs-lookup"><span data-stu-id="7c11e-285">Suppresses the banner.</span></span> <span data-ttu-id="7c11e-286">設為 `true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="7c11e-286">Set to `true` or `false`.</span></span>|  
|<span data-ttu-id="7c11e-287">help</span><span class="sxs-lookup"><span data-stu-id="7c11e-287">help</span></span>|<span data-ttu-id="7c11e-288">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="7c11e-288">Displays command syntax and options for the tool.</span></span> <span data-ttu-id="7c11e-289">設為 `true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="7c11e-289">Set to `true` or `false`.</span></span>|  
  
## <a name="examples"></a><span data-ttu-id="7c11e-290">範例</span><span class="sxs-lookup"><span data-stu-id="7c11e-290">Examples</span></span>  
 <span data-ttu-id="7c11e-291">下列命令會從 `myFile.xdr` 產生 XML 結構描述，並將它儲存到目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="7c11e-291">The following command generates an XML schema from `myFile.xdr` and saves it to the current directory.</span></span>  
  
```console  
xsd myFile.xdr   
```  
  
 <span data-ttu-id="7c11e-292">下列命令會從 `myFile.xml` 產生 XML 結構描述，並將它儲存到指定的目錄。</span><span class="sxs-lookup"><span data-stu-id="7c11e-292">The following command generates an XML schema from `myFile.xml` and saves it to the specified directory.</span></span>  
  
```console  
xsd myFile.xml /outputdir:myOutputDir  
```  
  
 <span data-ttu-id="7c11e-293">下列命令會產生對應到以 C# 語言指定之結構描述的資料集，並在目前的目錄中將它儲存為 `XSDSchemaFile.cs`。</span><span class="sxs-lookup"><span data-stu-id="7c11e-293">The following command generates a data set that corresponds to the specified schema in the C# language and saves it as `XSDSchemaFile.cs` in the current directory.</span></span>  
  
```console  
xsd /dataset /language:CS XSDSchemaFile.xsd  
```  
  
 <span data-ttu-id="7c11e-294">下列命令會對 `myAssembly.dll` 組件中的所有型別產生 XML 結構描述，並在目前的目錄中將它們儲存為 `schema0.xsd`。</span><span class="sxs-lookup"><span data-stu-id="7c11e-294">The following command generates XML schemas for all types in the assembly `myAssembly.dll` and saves them as `schema0.xsd` in the current directory.</span></span>  
  
```console  
xsd myAssembly.dll    
```  
  
## <a name="see-also"></a><span data-ttu-id="7c11e-295">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c11e-295">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
- [<span data-ttu-id="7c11e-296">工具</span><span class="sxs-lookup"><span data-stu-id="7c11e-296">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="7c11e-297">命令提示字元</span><span class="sxs-lookup"><span data-stu-id="7c11e-297">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
- [<span data-ttu-id="7c11e-298">LINQ to DataSet 概觀</span><span class="sxs-lookup"><span data-stu-id="7c11e-298">LINQ to DataSet Overview</span></span>](../../../docs/framework/data/adonet/linq-to-dataset-overview.md)
- [<span data-ttu-id="7c11e-299">查詢具類型資料集</span><span class="sxs-lookup"><span data-stu-id="7c11e-299">Querying Typed DataSets</span></span>](../../../docs/framework/data/adonet/querying-typed-datasets.md)
- [<span data-ttu-id="7c11e-300">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="7c11e-300">LINQ (Language-Integrated Query)</span></span>](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)
