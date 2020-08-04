---
title: SqlMetal.exe (程式碼產生工具)
description: 瞭解程式碼產生工具 SqlMetal.exe。 使用工具來產生 .NET LINQ to SQL 元件的程式碼和對應。
ms.date: 03/30/2017
helpviewer_keywords:
- SQLMetal [LINQ to SQL]
- code generation tool
- SQLMetal.exe
- LINQ to SQL, serialization
- LINQ to SQL, DBML files
- LINQ to SQL, SQLMetal
ms.assetid: 819e5a96-7646-4fdb-b14b-fe31221b0614
ms.openlocfilehash: 84cad85a7a9fc4b420b57543b7f258607be4ab52
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517044"
---
# <a name="sqlmetalexe-code-generation-tool"></a><span data-ttu-id="4bfa2-104">SqlMetal.exe (程式碼產生工具)</span><span class="sxs-lookup"><span data-stu-id="4bfa2-104">SqlMetal.exe (Code Generation Tool)</span></span>
<span data-ttu-id="4bfa2-105">SqlMetal 命令列工具會為 .NET Framework 的 [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] 元件產生程式碼及對應。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-105">The SqlMetal command-line tool generates code and mapping for the [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] component of the .NET Framework.</span></span> <span data-ttu-id="4bfa2-106">藉由套用本主題稍後出現的選項，您就可以指示 SqlMetal 執行數個不同的動作，包括以下各項：</span><span class="sxs-lookup"><span data-stu-id="4bfa2-106">By applying options that appear later in this topic, you can instruct SqlMetal to perform several different actions that include the following:</span></span>  
  
- <span data-ttu-id="4bfa2-107">從資料庫產生原始程式碼和對應屬性或對應檔。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-107">From a database, generate source code and mapping attributes or a mapping file.</span></span>  
  
- <span data-ttu-id="4bfa2-108">從資料庫產生中繼資料庫標記語言 (.dbml) 檔用於自訂。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-108">From a database, generate an intermediate database markup language (.dbml) file for customization.</span></span>  
  
- <span data-ttu-id="4bfa2-109">從 .dbml 檔產生程式碼和對應屬性或對應檔。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-109">From a .dbml file, generate code and mapping attributes or a mapping file.</span></span>  
  
 <span data-ttu-id="4bfa2-110">此工具會自動與 Visual Studio 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-110">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="4bfa2-111">根據預設，這個檔案位於 `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-111">By default, the file is located at `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span></span> <span data-ttu-id="4bfa2-112">如果您沒有安裝 Visual Studio，您也可以下載 [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225)以取得 SQLMetal 檔案。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-112">If you do not install Visual Studio, you can also get the SQLMetal file by downloading the [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4bfa2-113">使用 Visual Studio 的開發人員也可以使用物件關聯式設計工具來產生實體類別。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-113">Developers who use Visual Studio can also use the Object Relational Designer to generate entity classes.</span></span> <span data-ttu-id="4bfa2-114">命令列方法會針對大型資料庫做適當調整。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-114">The command-line approach scales well for large databases.</span></span> <span data-ttu-id="4bfa2-115">由於 SqlMetal 是命令列工具，因此您可以在建置處理序中使用它。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-115">Because SqlMetal is a command-line tool, you can use it in a build process.</span></span>  
  
 <span data-ttu-id="4bfa2-116">若要執行這項工具，請使用 [Visual Studio 開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-116">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="4bfa2-117">如需詳細資訊，請參閱[命令提示字元](developer-command-prompt-for-vs.md)。在命令提示字元中，鍵入下列命令：</span><span class="sxs-lookup"><span data-stu-id="4bfa2-117">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bfa2-118">Syntax</span><span class="sxs-lookup"><span data-stu-id="4bfa2-118">Syntax</span></span>  
  
```console  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a><span data-ttu-id="4bfa2-119">選項</span><span class="sxs-lookup"><span data-stu-id="4bfa2-119">Options</span></span>  
 <span data-ttu-id="4bfa2-120">若要檢視最新的選項清單，請進入安裝位置，並在命令提示字元輸入 `sqlmetal /?` 。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-120">To view the most current option list, type `sqlmetal /?` at a command prompt from the installed location.</span></span>  
  
 <span data-ttu-id="4bfa2-121">**連線選項**</span><span class="sxs-lookup"><span data-stu-id="4bfa2-121">**Connection Options**</span></span>  
  
|<span data-ttu-id="4bfa2-122">選項</span><span class="sxs-lookup"><span data-stu-id="4bfa2-122">Option</span></span>|<span data-ttu-id="4bfa2-123">說明</span><span class="sxs-lookup"><span data-stu-id="4bfa2-123">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4bfa2-124">\**/server：\*\*\*\<name>*</span><span class="sxs-lookup"><span data-stu-id="4bfa2-124">**/server:** *\<name>*</span></span>|<span data-ttu-id="4bfa2-125">指定資料庫伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-125">Specifies database server name.</span></span>|  
|<span data-ttu-id="4bfa2-126">\**/database：\*\*\*\<name>*</span><span class="sxs-lookup"><span data-stu-id="4bfa2-126">**/database:** *\<name>*</span></span>|<span data-ttu-id="4bfa2-127">指定伺服器上的資料庫目錄。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-127">Specifies database catalog on server.</span></span>|  
|<span data-ttu-id="4bfa2-128">\**/user：\*\*\*\<name>*</span><span class="sxs-lookup"><span data-stu-id="4bfa2-128">**/user:** *\<name>*</span></span>|<span data-ttu-id="4bfa2-129">指定登入使用者識別碼。預設值：使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-129">Specifies logon user id. Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="4bfa2-130">\**/password：\*\*\*\<password>*</span><span class="sxs-lookup"><span data-stu-id="4bfa2-130">**/password:** *\<password>*</span></span>|<span data-ttu-id="4bfa2-131">指定登入密碼。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-131">Specifies logon password.</span></span> <span data-ttu-id="4bfa2-132">預設值：使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-132">Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="4bfa2-133">\**/conn：\*\*\*\<connection string>*</span><span class="sxs-lookup"><span data-stu-id="4bfa2-133">**/conn:** *\<connection string>*</span></span>|<span data-ttu-id="4bfa2-134">指定資料庫連接字串。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-134">Specifies database connection string.</span></span> <span data-ttu-id="4bfa2-135">不可配合 **/server**、 **/database**、 **/user**或 **/password** 選項使用。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-135">Cannot be used with **/server**, **/database**, **/user**, or **/password** options.</span></span><br /><br /> <span data-ttu-id="4bfa2-136">不要在連接字串中包含檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-136">Do not include the file name in the connection string.</span></span> <span data-ttu-id="4bfa2-137">而是在命令列中加入檔名來做為輸入檔案。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-137">Instead, add the file name to the command line as the input file.</span></span> <span data-ttu-id="4bfa2-138">例如，下行指定 "c:\northwnd.mdf" 作為輸入檔案： **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-138">For example, the following line specifies "c:\northwnd.mdf" as the input file: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span></span>|  
|<span data-ttu-id="4bfa2-139">\**/timeout：\*\*\*\<seconds>*</span><span class="sxs-lookup"><span data-stu-id="4bfa2-139">**/timeout:** *\<seconds>*</span></span>|<span data-ttu-id="4bfa2-140">指定 SqlMetal 存取資料庫時的逾時值。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-140">Specifies time-out value when SqlMetal accesses the database.</span></span> <span data-ttu-id="4bfa2-141">預設值：0 (也就是沒有時間限制)。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-141">Default value: 0 (that is, no time limit).</span></span>|  
  
 <span data-ttu-id="4bfa2-142">**擷取選項**</span><span class="sxs-lookup"><span data-stu-id="4bfa2-142">**Extraction options**</span></span>  
  
|<span data-ttu-id="4bfa2-143">選項</span><span class="sxs-lookup"><span data-stu-id="4bfa2-143">Option</span></span>|<span data-ttu-id="4bfa2-144">說明</span><span class="sxs-lookup"><span data-stu-id="4bfa2-144">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4bfa2-145">**/views**</span><span class="sxs-lookup"><span data-stu-id="4bfa2-145">**/views**</span></span>|<span data-ttu-id="4bfa2-146">擷取資料庫檢視。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-146">Extracts database views.</span></span>|  
|<span data-ttu-id="4bfa2-147">**/functions**</span><span class="sxs-lookup"><span data-stu-id="4bfa2-147">**/functions**</span></span>|<span data-ttu-id="4bfa2-148">擷取資料庫函式。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-148">Extracts database functions.</span></span>|  
|<span data-ttu-id="4bfa2-149">**/sprocs**</span><span class="sxs-lookup"><span data-stu-id="4bfa2-149">**/sprocs**</span></span>|<span data-ttu-id="4bfa2-150">擷取預存程序。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-150">Extracts stored procedures.</span></span>|  
  
 <span data-ttu-id="4bfa2-151">**輸出選項**</span><span class="sxs-lookup"><span data-stu-id="4bfa2-151">**Output options**</span></span>  
  
|<span data-ttu-id="4bfa2-152">選項</span><span class="sxs-lookup"><span data-stu-id="4bfa2-152">Option</span></span>|<span data-ttu-id="4bfa2-153">說明</span><span class="sxs-lookup"><span data-stu-id="4bfa2-153">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4bfa2-154">**/dbml** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="4bfa2-154">**/dbml** *[:file]*</span></span>|<span data-ttu-id="4bfa2-155">以 .dbml 傳送輸出。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-155">Sends output as .dbml.</span></span> <span data-ttu-id="4bfa2-156">無法搭配 **/map** 選項使用。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-156">Cannot be used with **/map** option.</span></span>|  
|<span data-ttu-id="4bfa2-157">**/code** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="4bfa2-157">**/code** *[:file]*</span></span>|<span data-ttu-id="4bfa2-158">以原始程式碼傳送輸出。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-158">Sends output as source code.</span></span> <span data-ttu-id="4bfa2-159">無法搭配 **/dbml** 選項使用。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-159">Cannot be used with **/dbml** option.</span></span>|  
|<span data-ttu-id="4bfa2-160">**/map** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="4bfa2-160">**/map** *[:file]*</span></span>|<span data-ttu-id="4bfa2-161">產生 XML 對應檔而不是屬性。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-161">Generates an XML mapping file instead of attributes.</span></span> <span data-ttu-id="4bfa2-162">無法搭配 **/dbml** 選項使用。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-162">Cannot be used with **/dbml** option.</span></span>|  
  
 <span data-ttu-id="4bfa2-163">**其他**</span><span class="sxs-lookup"><span data-stu-id="4bfa2-163">**Miscellaneous**</span></span>  
  
|<span data-ttu-id="4bfa2-164">選項</span><span class="sxs-lookup"><span data-stu-id="4bfa2-164">Option</span></span>|<span data-ttu-id="4bfa2-165">說明</span><span class="sxs-lookup"><span data-stu-id="4bfa2-165">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4bfa2-166">\**/language：\*\*\*\<language>*</span><span class="sxs-lookup"><span data-stu-id="4bfa2-166">**/language:** *\<language>*</span></span>|<span data-ttu-id="4bfa2-167">指定原始程式碼語言。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-167">Specifies source code language.</span></span><br /><br /> <span data-ttu-id="4bfa2-168">有效 *\<language>* ： vb、csharp。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-168">Valid *\<language>*: vb, csharp.</span></span><br /><br /> <span data-ttu-id="4bfa2-169">預設值：衍生自程式碼檔案名稱的副檔名。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-169">Default value: Derived from extension on code file name.</span></span>|  
|<span data-ttu-id="4bfa2-170">\**/namespace：\*\*\*\<name>*</span><span class="sxs-lookup"><span data-stu-id="4bfa2-170">**/namespace:** *\<name>*</span></span>|<span data-ttu-id="4bfa2-171">指定所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-171">Specifies namespace of the generated code.</span></span> <span data-ttu-id="4bfa2-172">預設值：沒有命名空間。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-172">Default value: no namespace.</span></span>|  
|<span data-ttu-id="4bfa2-173">\**/coNtext：\*\*\*\<type>*</span><span class="sxs-lookup"><span data-stu-id="4bfa2-173">**/context:** *\<type>*</span></span>|<span data-ttu-id="4bfa2-174">指定資料庫內容類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-174">Specifies name of data context class.</span></span> <span data-ttu-id="4bfa2-175">預設值：衍生自資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-175">Default value: Derived from database name.</span></span>|  
|<span data-ttu-id="4bfa2-176">\**/entitybase：\*\*\*\<type>*</span><span class="sxs-lookup"><span data-stu-id="4bfa2-176">**/entitybase:** *\<type>*</span></span>|<span data-ttu-id="4bfa2-177">指定所產生程式碼中實體類別的基底類別。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-177">Specifies the base class of the entity classes in the generated code.</span></span> <span data-ttu-id="4bfa2-178">預設值：實體沒有基底類別。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-178">Default value: Entities have no base class.</span></span>|  
|<span data-ttu-id="4bfa2-179">**/pluralize**</span><span class="sxs-lookup"><span data-stu-id="4bfa2-179">**/pluralize**</span></span>|<span data-ttu-id="4bfa2-180">自動複數化或單數化類別和成員名稱。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-180">Automatically pluralizes or singularizes class and member names.</span></span><br /><br /> <span data-ttu-id="4bfa2-181">這個選項功能僅適用於美國英文版本。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-181">This option is available only in the U.S. English version.</span></span>|  
|<span data-ttu-id="4bfa2-182">\**/serialization：\*\*\*\<option>*</span><span class="sxs-lookup"><span data-stu-id="4bfa2-182">**/serialization:** *\<option>*</span></span>|<span data-ttu-id="4bfa2-183">產生可序列化的類別。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-183">Generates serializable classes.</span></span><br /><br /> <span data-ttu-id="4bfa2-184">有效 *\<option>* ：無、單向。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-184">Valid *\<option>*: None, Unidirectional.</span></span> <span data-ttu-id="4bfa2-185">預設值：無。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-185">Default value: None.</span></span><br /><br /> <span data-ttu-id="4bfa2-186">如需詳細資訊，請參閱[序列化](../data/adonet/sql/linq/serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-186">For more information, see [Serialization](../data/adonet/sql/linq/serialization.md).</span></span>|  
  
 <span data-ttu-id="4bfa2-187">**輸入檔**</span><span class="sxs-lookup"><span data-stu-id="4bfa2-187">**Input File**</span></span>  
  
|<span data-ttu-id="4bfa2-188">選項</span><span class="sxs-lookup"><span data-stu-id="4bfa2-188">Option</span></span>|<span data-ttu-id="4bfa2-189">說明</span><span class="sxs-lookup"><span data-stu-id="4bfa2-189">Description</span></span>|  
|------------|-----------------|  
|**\<input file>**|<span data-ttu-id="4bfa2-190">指定 SQL Server Express .mdf 檔、SQL Server Compact 3.5 .sdf 檔或 .dbml 中繼檔。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-190">Specifies a SQL Server Express .mdf file, a SQL Server Compact 3.5 .sdf file, or a .dbml intermediate file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bfa2-191">備註</span><span class="sxs-lookup"><span data-stu-id="4bfa2-191">Remarks</span></span>  
 <span data-ttu-id="4bfa2-192">SqlMetal 功能實際上包含兩個步驟：</span><span class="sxs-lookup"><span data-stu-id="4bfa2-192">SqlMetal functionality actually involves two steps:</span></span>  
  
- <span data-ttu-id="4bfa2-193">將資料庫的中繼資料擷取至 .dbml 檔。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-193">Extracting the metadata of the database into a .dbml file.</span></span>  
  
- <span data-ttu-id="4bfa2-194">產生程式碼輸出檔。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-194">Generating a code output file.</span></span>  
  
     <span data-ttu-id="4bfa2-195">使用適當的命令列選項，您就可以產生 Visual Basic 或 C# 原始程式碼，或是產生 XML 對應檔。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-195">By using the appropriate command-line options, you can produce Visual Basic or C# source code, or you can produce an XML mapping file.</span></span>  
  
 <span data-ttu-id="4bfa2-196">若要從 .mdf 檔擷取中繼資料，您必須在所有其他選項之後指定 .mdf 檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-196">To extract the metadata from an .mdf file, you must specify the name of the .mdf file after all other options.</span></span>  
  
 <span data-ttu-id="4bfa2-197">如果沒有指定 **/server** ，則會假設為 **localhost/sqlexpress** 。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-197">If no **/server** is specified, **localhost/sqlexpress** is assumed.</span></span>  
  
 <span data-ttu-id="4bfa2-198">如果下列其中一或多個條件為真，Microsoft SQL Server 2005 會擲回例外狀況：</span><span class="sxs-lookup"><span data-stu-id="4bfa2-198">Microsoft SQL Server 2005 throws an exception if one or more of the following conditions are true:</span></span>  
  
- <span data-ttu-id="4bfa2-199">SqlMetal 嘗試擷取呼叫本身的預存程序。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-199">SqlMetal tries to extract a stored procedure that calls itself.</span></span>  
  
- <span data-ttu-id="4bfa2-200">預存程序、函式或檢視的巢狀層超過 32。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-200">The nesting level of a stored procedure, function, or view exceeds 32.</span></span>  
  
     <span data-ttu-id="4bfa2-201">SqlMetal 會快取這個例外狀況並回報為警告。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-201">SqlMetal catches this exception and reports it as a warning.</span></span>  
  
 <span data-ttu-id="4bfa2-202">若要指定輸入檔案名稱，請將名稱以輸入檔案加入命令列。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-202">To specify an input file name, add the name to the command line as the input file.</span></span> <span data-ttu-id="4bfa2-203">不支援將檔案名稱包含在連接字串中 (使用 **/conn** 選項)。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-203">Including the file name in the connection string (using the **/conn** option) is not supported.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="4bfa2-204">範例</span><span class="sxs-lookup"><span data-stu-id="4bfa2-204">Examples</span></span>  
 <span data-ttu-id="4bfa2-205">產生 .dbml 檔，其中包含擷取的 SQL 中繼資料：</span><span class="sxs-lookup"><span data-stu-id="4bfa2-205">Generate a .dbml file that includes extracted SQL metadata:</span></span>  
  
 <span data-ttu-id="4bfa2-206">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span><span class="sxs-lookup"><span data-stu-id="4bfa2-206">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span></span>  
  
 <span data-ttu-id="4bfa2-207">產生 .dbml 檔，其中包括使用 SQL Server Express 從 .mdf 檔擷取的 SQL 中繼資料：</span><span class="sxs-lookup"><span data-stu-id="4bfa2-207">Generate a .dbml file that includes extracted SQL metadata from an .mdf file by using SQL Server Express:</span></span>  
  
 <span data-ttu-id="4bfa2-208">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span><span class="sxs-lookup"><span data-stu-id="4bfa2-208">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span></span>  
  
 <span data-ttu-id="4bfa2-209">產生 .dbml 檔，其中包括從 SQL Server Express 擷取的 SQL 中繼資料：</span><span class="sxs-lookup"><span data-stu-id="4bfa2-209">Generate a .dbml file that includes extracted SQL metadata from SQL Server Express:</span></span>  
  
 <span data-ttu-id="4bfa2-210">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span><span class="sxs-lookup"><span data-stu-id="4bfa2-210">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span></span>  
  
 <span data-ttu-id="4bfa2-211">從 .dbml 中繼資料檔產生原始程式碼：</span><span class="sxs-lookup"><span data-stu-id="4bfa2-211">Generate source code from a .dbml metadata file:</span></span>  
  
 <span data-ttu-id="4bfa2-212">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span><span class="sxs-lookup"><span data-stu-id="4bfa2-212">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span></span>  
  
 <span data-ttu-id="4bfa2-213">直接從 SQL 中繼資料產生原始程式碼：</span><span class="sxs-lookup"><span data-stu-id="4bfa2-213">Generate source code from SQL metadata directly:</span></span>  
  
 <span data-ttu-id="4bfa2-214">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span><span class="sxs-lookup"><span data-stu-id="4bfa2-214">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4bfa2-215">當您使用 **/pluralize** 選項搭配 Northwind 範例資料庫時，請注意以下行為：</span><span class="sxs-lookup"><span data-stu-id="4bfa2-215">When you use the **/pluralize** option with the Northwind sample database, note the following behavior.</span></span> <span data-ttu-id="4bfa2-216">當 SqlMetal 提供資料表的資料列類型名稱時，資料表名稱會是單數。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-216">When SqlMetal makes row-type names for tables, the table names are singular.</span></span> <span data-ttu-id="4bfa2-217">當它為資料表提供 <xref:System.Data.Linq.DataContext> 屬性時，資料表名稱會是複數。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-217">When it makes <xref:System.Data.Linq.DataContext> properties for tables, the table names are plural.</span></span> <span data-ttu-id="4bfa2-218">碰巧的是，Northwind 範例資料庫中的資料表已經是複數。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-218">Coincidentally, the tables in the Northwind sample database are already plural.</span></span> <span data-ttu-id="4bfa2-219">因此您不會看見該部分的運作情形。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-219">Therefore, you do not see that part working.</span></span> <span data-ttu-id="4bfa2-220">雖然一般會將資料庫資料表的名稱設為單數，在 .NET 中仍然常會把集合名稱設為複數。</span><span class="sxs-lookup"><span data-stu-id="4bfa2-220">Although it is common practice to name database tables singular, it is also a common practice in .NET to name collections plural.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bfa2-221">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4bfa2-221">See also</span></span>

- [<span data-ttu-id="4bfa2-222">作法：以 Visual Basic 或 C# 產生物件模型</span><span class="sxs-lookup"><span data-stu-id="4bfa2-222">How to: Generate the Object Model in Visual Basic or C#</span></span>](../data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
- [<span data-ttu-id="4bfa2-223">LINQ to SQL 中的程式碼產生</span><span class="sxs-lookup"><span data-stu-id="4bfa2-223">Code Generation in LINQ to SQL</span></span>](../data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="4bfa2-224">外部對應</span><span class="sxs-lookup"><span data-stu-id="4bfa2-224">External Mapping</span></span>](../data/adonet/sql/linq/external-mapping.md)
