---
title: SqlMetal.exe (程式碼產生工具)
ms.date: 03/30/2017
helpviewer_keywords:
- SQLMetal [LINQ to SQL]
- code generation tool
- SQLMetal.exe
- LINQ to SQL, serialization
- LINQ to SQL, DBML files
- LINQ to SQL, SQLMetal
ms.assetid: 819e5a96-7646-4fdb-b14b-fe31221b0614
ms.openlocfilehash: 94ed6328857f6e77cea150d69719322d3aaaea69
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45597242"
---
# <a name="sqlmetalexe-code-generation-tool"></a><span data-ttu-id="c747b-102">SqlMetal.exe (程式碼產生工具)</span><span class="sxs-lookup"><span data-stu-id="c747b-102">SqlMetal.exe (Code Generation Tool)</span></span>
<span data-ttu-id="c747b-103">SqlMetal 命令列工具會產生 [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] 之 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]元件的程式碼和對應。</span><span class="sxs-lookup"><span data-stu-id="c747b-103">The SqlMetal command-line tool generates code and mapping for the [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] component of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="c747b-104">藉由套用本主題稍後出現的選項，您就可以指示 SqlMetal 執行數個不同的動作，包括以下各項：</span><span class="sxs-lookup"><span data-stu-id="c747b-104">By applying options that appear later in this topic, you can instruct SqlMetal to perform several different actions that include the following:</span></span>  
  
-   <span data-ttu-id="c747b-105">從資料庫產生原始程式碼和對應屬性或對應檔。</span><span class="sxs-lookup"><span data-stu-id="c747b-105">From a database, generate source code and mapping attributes or a mapping file.</span></span>  
  
-   <span data-ttu-id="c747b-106">從資料庫產生中繼資料庫標記語言 (.dbml) 檔用於自訂。</span><span class="sxs-lookup"><span data-stu-id="c747b-106">From a database, generate an intermediate database markup language (.dbml) file for customization.</span></span>  
  
-   <span data-ttu-id="c747b-107">從 .dbml 檔產生程式碼和對應屬性或對應檔。</span><span class="sxs-lookup"><span data-stu-id="c747b-107">From a .dbml file, generate code and mapping attributes or a mapping file.</span></span>  
  
 <span data-ttu-id="c747b-108">此工具會自動與 Visual Studio 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="c747b-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="c747b-109">根據預設，這個檔案位於 `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin。</span><span class="sxs-lookup"><span data-stu-id="c747b-109">By default, the file is located at `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span></span> <span data-ttu-id="c747b-110">如果您沒有安裝 Visual Studio，您也可以下載 [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225)以取得 SQLMetal 檔案。</span><span class="sxs-lookup"><span data-stu-id="c747b-110">If you do not install Visual Studio, you can also get the SQLMetal file by downloading the [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c747b-111">使用 Visual Studio 的開發人員也可以使用 [!INCLUDE[vs_ordesigner_long](../../../includes/vs-ordesigner-long-md.md)] 來產生實體類別。</span><span class="sxs-lookup"><span data-stu-id="c747b-111">Developers who use Visual Studio can also use the [!INCLUDE[vs_ordesigner_long](../../../includes/vs-ordesigner-long-md.md)] to generate entity classes.</span></span> <span data-ttu-id="c747b-112">命令列方法會針對大型資料庫做適當調整。</span><span class="sxs-lookup"><span data-stu-id="c747b-112">The command-line approach scales well for large databases.</span></span> <span data-ttu-id="c747b-113">由於 SqlMetal 是命令列工具，因此您可以在建置處理序中使用它。</span><span class="sxs-lookup"><span data-stu-id="c747b-113">Because SqlMetal is a command-line tool, you can use it in a build process.</span></span>  
  
 <span data-ttu-id="c747b-114">若要執行此工具，請使用 [開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。</span><span class="sxs-lookup"><span data-stu-id="c747b-114">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="c747b-115">如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。在命令提示字元中，鍵入下列命令：</span><span class="sxs-lookup"><span data-stu-id="c747b-115">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c747b-116">語法</span><span class="sxs-lookup"><span data-stu-id="c747b-116">Syntax</span></span>  
  
```  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a><span data-ttu-id="c747b-117">選項</span><span class="sxs-lookup"><span data-stu-id="c747b-117">Options</span></span>  
 <span data-ttu-id="c747b-118">若要檢視最新的選項清單，請進入安裝位置，並在命令提示字元輸入 `sqlmetal /?` 。</span><span class="sxs-lookup"><span data-stu-id="c747b-118">To view the most current option list, type `sqlmetal /?` at a command prompt from the installed location.</span></span>  
  
 <span data-ttu-id="c747b-119">**連接選項**</span><span class="sxs-lookup"><span data-stu-id="c747b-119">**Connection Options**</span></span>  
  
|<span data-ttu-id="c747b-120">選項</span><span class="sxs-lookup"><span data-stu-id="c747b-120">Option</span></span>|<span data-ttu-id="c747b-121">描述</span><span class="sxs-lookup"><span data-stu-id="c747b-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c747b-122">**/server:** *\<名稱>*</span><span class="sxs-lookup"><span data-stu-id="c747b-122">**/server:** *\<name>*</span></span>|<span data-ttu-id="c747b-123">指定資料庫伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="c747b-123">Specifies database server name.</span></span>|  
|<span data-ttu-id="c747b-124">**/database:** *\<名稱>*</span><span class="sxs-lookup"><span data-stu-id="c747b-124">**/database:** *\<name>*</span></span>|<span data-ttu-id="c747b-125">指定伺服器上的資料庫目錄。</span><span class="sxs-lookup"><span data-stu-id="c747b-125">Specifies database catalog on server.</span></span>|  
|<span data-ttu-id="c747b-126">**/user:** *\<名稱>*</span><span class="sxs-lookup"><span data-stu-id="c747b-126">**/user:** *\<name>*</span></span>|<span data-ttu-id="c747b-127">指定登入使用者識別碼。預設值：使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="c747b-127">Specifies logon user id. Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="c747b-128">**/password:** *\<密碼>*</span><span class="sxs-lookup"><span data-stu-id="c747b-128">**/password:** *\<password>*</span></span>|<span data-ttu-id="c747b-129">指定登入密碼。</span><span class="sxs-lookup"><span data-stu-id="c747b-129">Specifies logon password.</span></span> <span data-ttu-id="c747b-130">預設值：使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="c747b-130">Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="c747b-131">**/conn:** *\<連接字串>*</span><span class="sxs-lookup"><span data-stu-id="c747b-131">**/conn:** *\<connection string>*</span></span>|<span data-ttu-id="c747b-132">指定資料庫連接字串。</span><span class="sxs-lookup"><span data-stu-id="c747b-132">Specifies database connection string.</span></span> <span data-ttu-id="c747b-133">不可配合 **/server**、 **/database**、 **/user**或 **/password** 選項使用。</span><span class="sxs-lookup"><span data-stu-id="c747b-133">Cannot be used with **/server**, **/database**, **/user**, or **/password** options.</span></span><br /><br /> <span data-ttu-id="c747b-134">不要在連接字串中包含檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="c747b-134">Do not include the file name in the connection string.</span></span> <span data-ttu-id="c747b-135">而是在命令列中加入檔名來做為輸入檔案。</span><span class="sxs-lookup"><span data-stu-id="c747b-135">Instead, add the file name to the command line as the input file.</span></span> <span data-ttu-id="c747b-136">例如，下行指定 "c:\northwnd.mdf" 作為輸入檔案： **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**。</span><span class="sxs-lookup"><span data-stu-id="c747b-136">For example, the following line specifies "c:\northwnd.mdf" as the input file: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span></span>|  
|<span data-ttu-id="c747b-137">**/timeout:** *\<秒>*</span><span class="sxs-lookup"><span data-stu-id="c747b-137">**/timeout:** *\<seconds>*</span></span>|<span data-ttu-id="c747b-138">指定 SqlMetal 存取資料庫時的逾時值。</span><span class="sxs-lookup"><span data-stu-id="c747b-138">Specifies time-out value when SqlMetal accesses the database.</span></span> <span data-ttu-id="c747b-139">預設值：0 (也就是沒有時間限制)。</span><span class="sxs-lookup"><span data-stu-id="c747b-139">Default value: 0 (that is, no time limit).</span></span>|  
  
 <span data-ttu-id="c747b-140">**擷取選項**</span><span class="sxs-lookup"><span data-stu-id="c747b-140">**Extraction options**</span></span>  
  
|<span data-ttu-id="c747b-141">選項</span><span class="sxs-lookup"><span data-stu-id="c747b-141">Option</span></span>|<span data-ttu-id="c747b-142">描述</span><span class="sxs-lookup"><span data-stu-id="c747b-142">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c747b-143">**/views**</span><span class="sxs-lookup"><span data-stu-id="c747b-143">**/views**</span></span>|<span data-ttu-id="c747b-144">擷取資料庫檢視。</span><span class="sxs-lookup"><span data-stu-id="c747b-144">Extracts database views.</span></span>|  
|<span data-ttu-id="c747b-145">**/functions**</span><span class="sxs-lookup"><span data-stu-id="c747b-145">**/functions**</span></span>|<span data-ttu-id="c747b-146">擷取資料庫函式。</span><span class="sxs-lookup"><span data-stu-id="c747b-146">Extracts database functions.</span></span>|  
|<span data-ttu-id="c747b-147">**/sprocs**</span><span class="sxs-lookup"><span data-stu-id="c747b-147">**/sprocs**</span></span>|<span data-ttu-id="c747b-148">擷取預存程序。</span><span class="sxs-lookup"><span data-stu-id="c747b-148">Extracts stored procedures.</span></span>|  
  
 <span data-ttu-id="c747b-149">**輸出選項**</span><span class="sxs-lookup"><span data-stu-id="c747b-149">**Output options**</span></span>  
  
|<span data-ttu-id="c747b-150">選項</span><span class="sxs-lookup"><span data-stu-id="c747b-150">Option</span></span>|<span data-ttu-id="c747b-151">描述</span><span class="sxs-lookup"><span data-stu-id="c747b-151">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c747b-152">**/dbml** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="c747b-152">**/dbml** *[:file]*</span></span>|<span data-ttu-id="c747b-153">以 .dbml 傳送輸出。</span><span class="sxs-lookup"><span data-stu-id="c747b-153">Sends output as .dbml.</span></span> <span data-ttu-id="c747b-154">無法搭配 **/map** 選項使用。</span><span class="sxs-lookup"><span data-stu-id="c747b-154">Cannot be used with **/map** option.</span></span>|  
|<span data-ttu-id="c747b-155">**/code** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="c747b-155">**/code** *[:file]*</span></span>|<span data-ttu-id="c747b-156">以原始程式碼傳送輸出。</span><span class="sxs-lookup"><span data-stu-id="c747b-156">Sends output as source code.</span></span> <span data-ttu-id="c747b-157">無法搭配 **/dbml** 選項使用。</span><span class="sxs-lookup"><span data-stu-id="c747b-157">Cannot be used with **/dbml** option.</span></span>|  
|<span data-ttu-id="c747b-158">**/map** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="c747b-158">**/map** *[:file]*</span></span>|<span data-ttu-id="c747b-159">產生 XML 對應檔而不是屬性。</span><span class="sxs-lookup"><span data-stu-id="c747b-159">Generates an XML mapping file instead of attributes.</span></span> <span data-ttu-id="c747b-160">無法搭配 **/dbml** 選項使用。</span><span class="sxs-lookup"><span data-stu-id="c747b-160">Cannot be used with **/dbml** option.</span></span>|  
  
 <span data-ttu-id="c747b-161">**其他**</span><span class="sxs-lookup"><span data-stu-id="c747b-161">**Miscellaneous**</span></span>  
  
|<span data-ttu-id="c747b-162">選項</span><span class="sxs-lookup"><span data-stu-id="c747b-162">Option</span></span>|<span data-ttu-id="c747b-163">描述</span><span class="sxs-lookup"><span data-stu-id="c747b-163">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c747b-164">**/language:** *\<語言>*</span><span class="sxs-lookup"><span data-stu-id="c747b-164">**/language:** *\<language>*</span></span>|<span data-ttu-id="c747b-165">指定原始程式碼語言。</span><span class="sxs-lookup"><span data-stu-id="c747b-165">Specifies source code language.</span></span><br /><br /> <span data-ttu-id="c747b-166">有效的 *\<語言>*：vb、csharp。</span><span class="sxs-lookup"><span data-stu-id="c747b-166">Valid *\<language>*: vb, csharp.</span></span><br /><br /> <span data-ttu-id="c747b-167">預設值：衍生自程式碼檔案名稱的副檔名。</span><span class="sxs-lookup"><span data-stu-id="c747b-167">Default value: Derived from extension on code file name.</span></span>|  
|<span data-ttu-id="c747b-168">**/namespace:** *\<名稱>*</span><span class="sxs-lookup"><span data-stu-id="c747b-168">**/namespace:** *\<name>*</span></span>|<span data-ttu-id="c747b-169">指定所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="c747b-169">Specifies namespace of the generated code.</span></span> <span data-ttu-id="c747b-170">預設值：沒有命名空間。</span><span class="sxs-lookup"><span data-stu-id="c747b-170">Default value: no namespace.</span></span>|  
|<span data-ttu-id="c747b-171">**/context:** *\<類型>*</span><span class="sxs-lookup"><span data-stu-id="c747b-171">**/context:** *\<type>*</span></span>|<span data-ttu-id="c747b-172">指定資料庫內容類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="c747b-172">Specifies name of data context class.</span></span> <span data-ttu-id="c747b-173">預設值：衍生自資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="c747b-173">Default value: Derived from database name.</span></span>|  
|<span data-ttu-id="c747b-174">**/entitybase:** *\<類型>*</span><span class="sxs-lookup"><span data-stu-id="c747b-174">**/entitybase:** *\<type>*</span></span>|<span data-ttu-id="c747b-175">指定所產生程式碼中實體類別的基底類別。</span><span class="sxs-lookup"><span data-stu-id="c747b-175">Specifies the base class of the entity classes in the generated code.</span></span> <span data-ttu-id="c747b-176">預設值：實體沒有基底類別。</span><span class="sxs-lookup"><span data-stu-id="c747b-176">Default value: Entities have no base class.</span></span>|  
|<span data-ttu-id="c747b-177">**/pluralize**</span><span class="sxs-lookup"><span data-stu-id="c747b-177">**/pluralize**</span></span>|<span data-ttu-id="c747b-178">自動複數化或單數化類別和成員名稱。</span><span class="sxs-lookup"><span data-stu-id="c747b-178">Automatically pluralizes or singularizes class and member names.</span></span><br /><br /> <span data-ttu-id="c747b-179">這個選項功能僅適用於美國英文版本。</span><span class="sxs-lookup"><span data-stu-id="c747b-179">This option is available only in the U.S. English version.</span></span>|  
|<span data-ttu-id="c747b-180">**/serialization:** *\<選項>*</span><span class="sxs-lookup"><span data-stu-id="c747b-180">**/serialization:** *\<option>*</span></span>|<span data-ttu-id="c747b-181">產生可序列化的類別。</span><span class="sxs-lookup"><span data-stu-id="c747b-181">Generates serializable classes.</span></span><br /><br /> <span data-ttu-id="c747b-182">有效的 *\<選項>*：無、單向。</span><span class="sxs-lookup"><span data-stu-id="c747b-182">Valid *\<option>*: None, Unidirectional.</span></span> <span data-ttu-id="c747b-183">預設值：無。</span><span class="sxs-lookup"><span data-stu-id="c747b-183">Default value: None.</span></span><br /><br /> <span data-ttu-id="c747b-184">如需詳細資訊，請參閱[序列化](../../../docs/framework/data/adonet/sql/linq/serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="c747b-184">For more information, see [Serialization](../../../docs/framework/data/adonet/sql/linq/serialization.md).</span></span>|  
  
 <span data-ttu-id="c747b-185">**輸入檔案**</span><span class="sxs-lookup"><span data-stu-id="c747b-185">**Input File**</span></span>  
  
|<span data-ttu-id="c747b-186">選項</span><span class="sxs-lookup"><span data-stu-id="c747b-186">Option</span></span>|<span data-ttu-id="c747b-187">描述</span><span class="sxs-lookup"><span data-stu-id="c747b-187">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="c747b-188">**\<輸入檔>**</span><span class="sxs-lookup"><span data-stu-id="c747b-188">**\<input file>**</span></span>|<span data-ttu-id="c747b-189">指定 SQL Server Express .mdf 檔、 [!INCLUDE[ssEW](../../../includes/ssew-md.md)] .sdf 檔或是 .dbml 中繼檔。</span><span class="sxs-lookup"><span data-stu-id="c747b-189">Specifies a SQL Server Express .mdf file, a [!INCLUDE[ssEW](../../../includes/ssew-md.md)] .sdf file, or a .dbml intermediate file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c747b-190">備註</span><span class="sxs-lookup"><span data-stu-id="c747b-190">Remarks</span></span>  
 <span data-ttu-id="c747b-191">SqlMetal 功能實際上包含兩個步驟：</span><span class="sxs-lookup"><span data-stu-id="c747b-191">SqlMetal functionality actually involves two steps:</span></span>  
  
-   <span data-ttu-id="c747b-192">將資料庫的中繼資料擷取至 .dbml 檔。</span><span class="sxs-lookup"><span data-stu-id="c747b-192">Extracting the metadata of the database into a .dbml file.</span></span>  
  
-   <span data-ttu-id="c747b-193">產生程式碼輸出檔。</span><span class="sxs-lookup"><span data-stu-id="c747b-193">Generating a code output file.</span></span>  
  
     <span data-ttu-id="c747b-194">使用適當的命令列選項，您就可以產生 Visual Basic 或 C# 原始程式碼，或是產生 XML 對應檔。</span><span class="sxs-lookup"><span data-stu-id="c747b-194">By using the appropriate command-line options, you can produce Visual Basic or C# source code, or you can produce an XML mapping file.</span></span>  
  
 <span data-ttu-id="c747b-195">若要從 .mdf 檔擷取中繼資料，您必須在所有其他選項之後指定 .mdf 檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="c747b-195">To extract the metadata from an .mdf file, you must specify the name of the .mdf file after all other options.</span></span>  
  
 <span data-ttu-id="c747b-196">如果沒有指定 **/server** ，則會假設為 **localhost/sqlexpress** 。</span><span class="sxs-lookup"><span data-stu-id="c747b-196">If no **/server** is specified, **localhost/sqlexpress** is assumed.</span></span>  
  
 <span data-ttu-id="c747b-197">如果下列其中一個或多個條件為真，則[!INCLUDE[sqprsqext](../../../includes/sqprsqext-md.md)] 會擲回例外狀況：</span><span class="sxs-lookup"><span data-stu-id="c747b-197">[!INCLUDE[sqprsqext](../../../includes/sqprsqext-md.md)] throws an exception if one or more of the following conditions are true:</span></span>  
  
-   <span data-ttu-id="c747b-198">SqlMetal 嘗試擷取呼叫本身的預存程序。</span><span class="sxs-lookup"><span data-stu-id="c747b-198">SqlMetal tries to extract a stored procedure that calls itself.</span></span>  
  
-   <span data-ttu-id="c747b-199">預存程序、函式或檢視的巢狀層超過 32。</span><span class="sxs-lookup"><span data-stu-id="c747b-199">The nesting level of a stored procedure, function, or view exceeds 32.</span></span>  
  
     <span data-ttu-id="c747b-200">SqlMetal 會快取這個例外狀況並回報為警告。</span><span class="sxs-lookup"><span data-stu-id="c747b-200">SqlMetal catches this exception and reports it as a warning.</span></span>  
  
 <span data-ttu-id="c747b-201">若要指定輸入檔案名稱，請將名稱以輸入檔案加入命令列。</span><span class="sxs-lookup"><span data-stu-id="c747b-201">To specify an input file name, add the name to the command line as the input file.</span></span> <span data-ttu-id="c747b-202">不支援將檔案名稱包含在連接字串中 (使用 **/conn** 選項)。</span><span class="sxs-lookup"><span data-stu-id="c747b-202">Including the file name in the connection string (using the **/conn** option) is not supported.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c747b-203">範例</span><span class="sxs-lookup"><span data-stu-id="c747b-203">Examples</span></span>  
 <span data-ttu-id="c747b-204">產生 .dbml 檔，其中包含擷取的 SQL 中繼資料：</span><span class="sxs-lookup"><span data-stu-id="c747b-204">Generate a .dbml file that includes extracted SQL metadata:</span></span>  
  
 <span data-ttu-id="c747b-205">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span><span class="sxs-lookup"><span data-stu-id="c747b-205">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span></span>  
  
 <span data-ttu-id="c747b-206">產生 .dbml 檔，其中包括使用 SQL Server Express 從 .mdf 檔擷取的 SQL 中繼資料：</span><span class="sxs-lookup"><span data-stu-id="c747b-206">Generate a .dbml file that includes extracted SQL metadata from an .mdf file by using SQL Server Express:</span></span>  
  
 <span data-ttu-id="c747b-207">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span><span class="sxs-lookup"><span data-stu-id="c747b-207">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span></span>  
  
 <span data-ttu-id="c747b-208">產生 .dbml 檔，其中包括從 SQL Server Express 擷取的 SQL 中繼資料：</span><span class="sxs-lookup"><span data-stu-id="c747b-208">Generate a .dbml file that includes extracted SQL metadata from SQL Server Express:</span></span>  
  
 <span data-ttu-id="c747b-209">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span><span class="sxs-lookup"><span data-stu-id="c747b-209">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span></span>  
  
 <span data-ttu-id="c747b-210">從 .dbml 中繼資料檔產生原始程式碼：</span><span class="sxs-lookup"><span data-stu-id="c747b-210">Generate source code from a .dbml metadata file:</span></span>  
  
 <span data-ttu-id="c747b-211">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span><span class="sxs-lookup"><span data-stu-id="c747b-211">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span></span>  
  
 <span data-ttu-id="c747b-212">直接從 SQL 中繼資料產生原始程式碼：</span><span class="sxs-lookup"><span data-stu-id="c747b-212">Generate source code from SQL metadata directly:</span></span>  
  
 <span data-ttu-id="c747b-213">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span><span class="sxs-lookup"><span data-stu-id="c747b-213">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c747b-214">當您使用 **/pluralize** 選項搭配 Northwind 範例資料庫時，請注意以下行為：</span><span class="sxs-lookup"><span data-stu-id="c747b-214">When you use the **/pluralize** option with the Northwind sample database, note the following behavior.</span></span> <span data-ttu-id="c747b-215">當 SqlMetal 提供資料表的資料列類型名稱時，資料表名稱會是單數。</span><span class="sxs-lookup"><span data-stu-id="c747b-215">When SqlMetal makes row-type names for tables, the table names are singular.</span></span> <span data-ttu-id="c747b-216">當它為資料表提供 <xref:System.Data.Linq.DataContext> 屬性時，資料表名稱會是複數。</span><span class="sxs-lookup"><span data-stu-id="c747b-216">When it makes <xref:System.Data.Linq.DataContext> properties for tables, the table names are plural.</span></span> <span data-ttu-id="c747b-217">碰巧的是，Northwind 範例資料庫中的資料表已經是複數。</span><span class="sxs-lookup"><span data-stu-id="c747b-217">Coincidentally, the tables in the Northwind sample database are already plural.</span></span> <span data-ttu-id="c747b-218">因此您不會看見該部分的運作情形。</span><span class="sxs-lookup"><span data-stu-id="c747b-218">Therefore, you do not see that part working.</span></span> <span data-ttu-id="c747b-219">雖然一般會將資料庫資料表的名稱設為單數，在 .NET 中仍然常會把集合名稱設為複數。</span><span class="sxs-lookup"><span data-stu-id="c747b-219">Although it is common practice to name database tables singular, it is also a common practice in .NET to name collections plural.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c747b-220">請參閱</span><span class="sxs-lookup"><span data-stu-id="c747b-220">See Also</span></span>  
 [<span data-ttu-id="c747b-221">如何：以 Visual Basic 或 C# 產生物件模型</span><span class="sxs-lookup"><span data-stu-id="c747b-221">How to: Generate the Object Model in Visual Basic or C#</span></span>](../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)  
 [<span data-ttu-id="c747b-222">LINQ to SQL 中的程式碼產生</span><span class="sxs-lookup"><span data-stu-id="c747b-222">Code Generation in LINQ to SQL</span></span>](../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [<span data-ttu-id="c747b-223">外部對應</span><span class="sxs-lookup"><span data-stu-id="c747b-223">External Mapping</span></span>](../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
