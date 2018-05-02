---
title: SqlMetal.exe (程式碼產生工具)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLMetal [LINQ to SQL]
- code generation tool
- SQLMetal.exe
- LINQ to SQL, serialization
- LINQ to SQL, DBML files
- LINQ to SQL, SQLMetal
ms.assetid: 819e5a96-7646-4fdb-b14b-fe31221b0614
caps.latest.revision: 43
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5c21c08cf76143959d11498594fbc94fb1dac55c
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="sqlmetalexe-code-generation-tool"></a><span data-ttu-id="a6857-102">SqlMetal.exe (程式碼產生工具)</span><span class="sxs-lookup"><span data-stu-id="a6857-102">SqlMetal.exe (Code Generation Tool)</span></span>
<span data-ttu-id="a6857-103">SqlMetal 命令列工具會產生 [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] 之 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]元件的程式碼和對應。</span><span class="sxs-lookup"><span data-stu-id="a6857-103">The SqlMetal command-line tool generates code and mapping for the [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] component of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="a6857-104">藉由套用本主題稍後出現的選項，您就可以指示 SqlMetal 執行數個不同的動作，包括以下各項：</span><span class="sxs-lookup"><span data-stu-id="a6857-104">By applying options that appear later in this topic, you can instruct SqlMetal to perform several different actions that include the following:</span></span>  
  
-   <span data-ttu-id="a6857-105">從資料庫產生原始程式碼和對應屬性或對應檔。</span><span class="sxs-lookup"><span data-stu-id="a6857-105">From a database, generate source code and mapping attributes or a mapping file.</span></span>  
  
-   <span data-ttu-id="a6857-106">從資料庫產生中繼資料庫標記語言 (.dbml) 檔用於自訂。</span><span class="sxs-lookup"><span data-stu-id="a6857-106">From a database, generate an intermediate database markup language (.dbml) file for customization.</span></span>  
  
-   <span data-ttu-id="a6857-107">從 .dbml 檔產生程式碼和對應屬性或對應檔。</span><span class="sxs-lookup"><span data-stu-id="a6857-107">From a .dbml file, generate code and mapping attributes or a mapping file.</span></span>  
  
 <span data-ttu-id="a6857-108">此工具會自動與 Visual Studio 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="a6857-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="a6857-109">根據預設，這個檔案位於 `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin。</span><span class="sxs-lookup"><span data-stu-id="a6857-109">By default, the file is located at `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span></span> <span data-ttu-id="a6857-110">如果您沒有安裝 Visual Studio，您也可以下載 [Windows SDK](http://go.microsoft.com/fwlink/?LinkId=142225)以取得 SQLMetal 檔案。</span><span class="sxs-lookup"><span data-stu-id="a6857-110">If you do not install Visual Studio, you can also get the SQLMetal file by downloading the [Windows SDK](http://go.microsoft.com/fwlink/?LinkId=142225).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6857-111">使用 Visual Studio 的開發人員也可以使用 [!INCLUDE[vs_ordesigner_long](../../../includes/vs-ordesigner-long-md.md)] 來產生實體類別。</span><span class="sxs-lookup"><span data-stu-id="a6857-111">Developers who use Visual Studio can also use the [!INCLUDE[vs_ordesigner_long](../../../includes/vs-ordesigner-long-md.md)] to generate entity classes.</span></span> <span data-ttu-id="a6857-112">命令列方法會針對大型資料庫做適當調整。</span><span class="sxs-lookup"><span data-stu-id="a6857-112">The command-line approach scales well for large databases.</span></span> <span data-ttu-id="a6857-113">由於 SqlMetal 是命令列工具，因此您可以在建置處理序中使用它。</span><span class="sxs-lookup"><span data-stu-id="a6857-113">Because SqlMetal is a command-line tool, you can use it in a build process.</span></span>  
  
 <span data-ttu-id="a6857-114">若要執行此工具，請使用 [開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。</span><span class="sxs-lookup"><span data-stu-id="a6857-114">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="a6857-115">如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。在命令提示字元中，鍵入下列命令：</span><span class="sxs-lookup"><span data-stu-id="a6857-115">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6857-116">語法</span><span class="sxs-lookup"><span data-stu-id="a6857-116">Syntax</span></span>  
  
```  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a><span data-ttu-id="a6857-117">選項</span><span class="sxs-lookup"><span data-stu-id="a6857-117">Options</span></span>  
 <span data-ttu-id="a6857-118">若要檢視最新的選項清單，請進入安裝位置，並在命令提示字元輸入 `sqlmetal /?` 。</span><span class="sxs-lookup"><span data-stu-id="a6857-118">To view the most current option list, type `sqlmetal /?` at a command prompt from the installed location.</span></span>  
  
 <span data-ttu-id="a6857-119">**連接選項**</span><span class="sxs-lookup"><span data-stu-id="a6857-119">**Connection Options**</span></span>  
  
|<span data-ttu-id="a6857-120">選項</span><span class="sxs-lookup"><span data-stu-id="a6857-120">Option</span></span>|<span data-ttu-id="a6857-121">描述</span><span class="sxs-lookup"><span data-stu-id="a6857-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a6857-122">**/server:** *\<名稱>*</span><span class="sxs-lookup"><span data-stu-id="a6857-122">**/server:** *\<name>*</span></span>|<span data-ttu-id="a6857-123">指定資料庫伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="a6857-123">Specifies database server name.</span></span>|  
|<span data-ttu-id="a6857-124">**/database:** *\<名稱>*</span><span class="sxs-lookup"><span data-stu-id="a6857-124">**/database:** *\<name>*</span></span>|<span data-ttu-id="a6857-125">指定伺服器上的資料庫目錄。</span><span class="sxs-lookup"><span data-stu-id="a6857-125">Specifies database catalog on server.</span></span>|  
|<span data-ttu-id="a6857-126">**/user:** *\<名稱>*</span><span class="sxs-lookup"><span data-stu-id="a6857-126">**/user:** *\<name>*</span></span>|<span data-ttu-id="a6857-127">指定登入使用者識別碼。預設值：使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="a6857-127">Specifies logon user id. Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="a6857-128">**/password:** *\<密碼>*</span><span class="sxs-lookup"><span data-stu-id="a6857-128">**/password:** *\<password>*</span></span>|<span data-ttu-id="a6857-129">指定登入密碼。</span><span class="sxs-lookup"><span data-stu-id="a6857-129">Specifies logon password.</span></span> <span data-ttu-id="a6857-130">預設值：使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="a6857-130">Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="a6857-131">**/conn:** *\<連接字串>*</span><span class="sxs-lookup"><span data-stu-id="a6857-131">**/conn:** *\<connection string>*</span></span>|<span data-ttu-id="a6857-132">指定資料庫連接字串。</span><span class="sxs-lookup"><span data-stu-id="a6857-132">Specifies database connection string.</span></span> <span data-ttu-id="a6857-133">不可配合 **/server**、 **/database**、 **/user**或 **/password** 選項使用。</span><span class="sxs-lookup"><span data-stu-id="a6857-133">Cannot be used with **/server**, **/database**, **/user**, or **/password** options.</span></span><br /><br /> <span data-ttu-id="a6857-134">不要在連接字串中包含檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="a6857-134">Do not include the file name in the connection string.</span></span> <span data-ttu-id="a6857-135">而是在命令列中加入檔名來做為輸入檔案。</span><span class="sxs-lookup"><span data-stu-id="a6857-135">Instead, add the file name to the command line as the input file.</span></span> <span data-ttu-id="a6857-136">例如，下行指定 "c:\northwnd.mdf" 作為輸入檔案： **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**。</span><span class="sxs-lookup"><span data-stu-id="a6857-136">For example, the following line specifies "c:\northwnd.mdf" as the input file: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span></span>|  
|<span data-ttu-id="a6857-137">**/timeout:** *\<秒>*</span><span class="sxs-lookup"><span data-stu-id="a6857-137">**/timeout:** *\<seconds>*</span></span>|<span data-ttu-id="a6857-138">指定 SqlMetal 存取資料庫時的逾時值。</span><span class="sxs-lookup"><span data-stu-id="a6857-138">Specifies time-out value when SqlMetal accesses the database.</span></span> <span data-ttu-id="a6857-139">預設值：0 (也就是沒有時間限制)。</span><span class="sxs-lookup"><span data-stu-id="a6857-139">Default value: 0 (that is, no time limit).</span></span>|  
  
 <span data-ttu-id="a6857-140">**擷取選項**</span><span class="sxs-lookup"><span data-stu-id="a6857-140">**Extraction options**</span></span>  
  
|<span data-ttu-id="a6857-141">選項</span><span class="sxs-lookup"><span data-stu-id="a6857-141">Option</span></span>|<span data-ttu-id="a6857-142">描述</span><span class="sxs-lookup"><span data-stu-id="a6857-142">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a6857-143">**/views**</span><span class="sxs-lookup"><span data-stu-id="a6857-143">**/views**</span></span>|<span data-ttu-id="a6857-144">擷取資料庫檢視。</span><span class="sxs-lookup"><span data-stu-id="a6857-144">Extracts database views.</span></span>|  
|<span data-ttu-id="a6857-145">**/functions**</span><span class="sxs-lookup"><span data-stu-id="a6857-145">**/functions**</span></span>|<span data-ttu-id="a6857-146">擷取資料庫函式。</span><span class="sxs-lookup"><span data-stu-id="a6857-146">Extracts database functions.</span></span>|  
|<span data-ttu-id="a6857-147">**/sprocs**</span><span class="sxs-lookup"><span data-stu-id="a6857-147">**/sprocs**</span></span>|<span data-ttu-id="a6857-148">擷取預存程序。</span><span class="sxs-lookup"><span data-stu-id="a6857-148">Extracts stored procedures.</span></span>|  
  
 <span data-ttu-id="a6857-149">**輸出選項**</span><span class="sxs-lookup"><span data-stu-id="a6857-149">**Output options**</span></span>  
  
|<span data-ttu-id="a6857-150">選項</span><span class="sxs-lookup"><span data-stu-id="a6857-150">Option</span></span>|<span data-ttu-id="a6857-151">描述</span><span class="sxs-lookup"><span data-stu-id="a6857-151">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a6857-152">**/dbml** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="a6857-152">**/dbml** *[:file]*</span></span>|<span data-ttu-id="a6857-153">以 .dbml 傳送輸出。</span><span class="sxs-lookup"><span data-stu-id="a6857-153">Sends output as .dbml.</span></span> <span data-ttu-id="a6857-154">無法搭配 **/map** 選項使用。</span><span class="sxs-lookup"><span data-stu-id="a6857-154">Cannot be used with **/map** option.</span></span>|  
|<span data-ttu-id="a6857-155">**/code** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="a6857-155">**/code** *[:file]*</span></span>|<span data-ttu-id="a6857-156">以原始程式碼傳送輸出。</span><span class="sxs-lookup"><span data-stu-id="a6857-156">Sends output as source code.</span></span> <span data-ttu-id="a6857-157">無法搭配 **/dbml** 選項使用。</span><span class="sxs-lookup"><span data-stu-id="a6857-157">Cannot be used with **/dbml** option.</span></span>|  
|<span data-ttu-id="a6857-158">**/map** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="a6857-158">**/map** *[:file]*</span></span>|<span data-ttu-id="a6857-159">產生 XML 對應檔而不是屬性。</span><span class="sxs-lookup"><span data-stu-id="a6857-159">Generates an XML mapping file instead of attributes.</span></span> <span data-ttu-id="a6857-160">無法搭配 **/dbml** 選項使用。</span><span class="sxs-lookup"><span data-stu-id="a6857-160">Cannot be used with **/dbml** option.</span></span>|  
  
 <span data-ttu-id="a6857-161">**其他**</span><span class="sxs-lookup"><span data-stu-id="a6857-161">**Miscellaneous**</span></span>  
  
|<span data-ttu-id="a6857-162">選項</span><span class="sxs-lookup"><span data-stu-id="a6857-162">Option</span></span>|<span data-ttu-id="a6857-163">描述</span><span class="sxs-lookup"><span data-stu-id="a6857-163">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a6857-164">**/language:** *\<語言>*</span><span class="sxs-lookup"><span data-stu-id="a6857-164">**/language:** *\<language>*</span></span>|<span data-ttu-id="a6857-165">指定原始程式碼語言。</span><span class="sxs-lookup"><span data-stu-id="a6857-165">Specifies source code language.</span></span><br /><br /> <span data-ttu-id="a6857-166">有效的 *\<語言>*：vb、csharp。</span><span class="sxs-lookup"><span data-stu-id="a6857-166">Valid *\<language>*: vb, csharp.</span></span><br /><br /> <span data-ttu-id="a6857-167">預設值：衍生自程式碼檔案名稱的副檔名。</span><span class="sxs-lookup"><span data-stu-id="a6857-167">Default value: Derived from extension on code file name.</span></span>|  
|<span data-ttu-id="a6857-168">**/namespace:** *\<名稱>*</span><span class="sxs-lookup"><span data-stu-id="a6857-168">**/namespace:** *\<name>*</span></span>|<span data-ttu-id="a6857-169">指定所產生程式碼的命名空間。</span><span class="sxs-lookup"><span data-stu-id="a6857-169">Specifies namespace of the generated code.</span></span> <span data-ttu-id="a6857-170">預設值：沒有命名空間。</span><span class="sxs-lookup"><span data-stu-id="a6857-170">Default value: no namespace.</span></span>|  
|<span data-ttu-id="a6857-171">**/context:** *\<類型>*</span><span class="sxs-lookup"><span data-stu-id="a6857-171">**/context:** *\<type>*</span></span>|<span data-ttu-id="a6857-172">指定資料庫內容類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="a6857-172">Specifies name of data context class.</span></span> <span data-ttu-id="a6857-173">預設值：衍生自資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="a6857-173">Default value: Derived from database name.</span></span>|  
|<span data-ttu-id="a6857-174">**/entitybase:** *\<類型>*</span><span class="sxs-lookup"><span data-stu-id="a6857-174">**/entitybase:** *\<type>*</span></span>|<span data-ttu-id="a6857-175">指定所產生程式碼中實體類別的基底類別。</span><span class="sxs-lookup"><span data-stu-id="a6857-175">Specifies the base class of the entity classes in the generated code.</span></span> <span data-ttu-id="a6857-176">預設值：實體沒有基底類別。</span><span class="sxs-lookup"><span data-stu-id="a6857-176">Default value: Entities have no base class.</span></span>|  
|<span data-ttu-id="a6857-177">**/pluralize**</span><span class="sxs-lookup"><span data-stu-id="a6857-177">**/pluralize**</span></span>|<span data-ttu-id="a6857-178">自動複數化或單數化類別和成員名稱。</span><span class="sxs-lookup"><span data-stu-id="a6857-178">Automatically pluralizes or singularizes class and member names.</span></span><br /><br /> <span data-ttu-id="a6857-179">這個選項功能僅適用於美國英文版本。</span><span class="sxs-lookup"><span data-stu-id="a6857-179">This option is available only in the U.S. English version.</span></span>|  
|<span data-ttu-id="a6857-180">**/serialization:** *\<選項>*</span><span class="sxs-lookup"><span data-stu-id="a6857-180">**/serialization:** *\<option>*</span></span>|<span data-ttu-id="a6857-181">產生可序列化的類別。</span><span class="sxs-lookup"><span data-stu-id="a6857-181">Generates serializable classes.</span></span><br /><br /> <span data-ttu-id="a6857-182">有效的 *\<選項>*：無、單向。</span><span class="sxs-lookup"><span data-stu-id="a6857-182">Valid *\<option>*: None, Unidirectional.</span></span> <span data-ttu-id="a6857-183">預設值：無。</span><span class="sxs-lookup"><span data-stu-id="a6857-183">Default value: None.</span></span><br /><br /> <span data-ttu-id="a6857-184">如需詳細資訊，請參閱[序列化](../../../docs/framework/data/adonet/sql/linq/serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="a6857-184">For more information, see [Serialization](../../../docs/framework/data/adonet/sql/linq/serialization.md).</span></span>|  
  
 <span data-ttu-id="a6857-185">**輸入檔案**</span><span class="sxs-lookup"><span data-stu-id="a6857-185">**Input File**</span></span>  
  
|<span data-ttu-id="a6857-186">選項</span><span class="sxs-lookup"><span data-stu-id="a6857-186">Option</span></span>|<span data-ttu-id="a6857-187">描述</span><span class="sxs-lookup"><span data-stu-id="a6857-187">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a6857-188">**\<輸入檔>**</span><span class="sxs-lookup"><span data-stu-id="a6857-188">**\<input file>**</span></span>|<span data-ttu-id="a6857-189">指定 SQL Server Express .mdf 檔、 [!INCLUDE[ssEW](../../../includes/ssew-md.md)] .sdf 檔或是 .dbml 中繼檔。</span><span class="sxs-lookup"><span data-stu-id="a6857-189">Specifies a SQL Server Express .mdf file, a [!INCLUDE[ssEW](../../../includes/ssew-md.md)] .sdf file, or a .dbml intermediate file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6857-190">備註</span><span class="sxs-lookup"><span data-stu-id="a6857-190">Remarks</span></span>  
 <span data-ttu-id="a6857-191">SqlMetal 功能實際上包含兩個步驟：</span><span class="sxs-lookup"><span data-stu-id="a6857-191">SqlMetal functionality actually involves two steps:</span></span>  
  
-   <span data-ttu-id="a6857-192">將資料庫的中繼資料擷取至 .dbml 檔。</span><span class="sxs-lookup"><span data-stu-id="a6857-192">Extracting the metadata of the database into a .dbml file.</span></span>  
  
-   <span data-ttu-id="a6857-193">產生程式碼輸出檔。</span><span class="sxs-lookup"><span data-stu-id="a6857-193">Generating a code output file.</span></span>  
  
     <span data-ttu-id="a6857-194">使用適當的命令列選項，您就可以產生 Visual Basic 或 C# 原始程式碼，或是產生 XML 對應檔。</span><span class="sxs-lookup"><span data-stu-id="a6857-194">By using the appropriate command-line options, you can produce Visual Basic or C# source code, or you can produce an XML mapping file.</span></span>  
  
 <span data-ttu-id="a6857-195">若要從 .mdf 檔擷取中繼資料，您必須在所有其他選項之後指定 .mdf 檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="a6857-195">To extract the metadata from an .mdf file, you must specify the name of the .mdf file after all other options.</span></span>  
  
 <span data-ttu-id="a6857-196">如果沒有指定 **/server** ，則會假設為 **localhost/sqlexpress** 。</span><span class="sxs-lookup"><span data-stu-id="a6857-196">If no **/server** is specified, **localhost/sqlexpress** is assumed.</span></span>  
  
 <span data-ttu-id="a6857-197">如果下列其中一個或多個條件為真，則[!INCLUDE[sqprsqext](../../../includes/sqprsqext-md.md)] 會擲回例外狀況：</span><span class="sxs-lookup"><span data-stu-id="a6857-197">[!INCLUDE[sqprsqext](../../../includes/sqprsqext-md.md)] throws an exception if one or more of the following conditions are true:</span></span>  
  
-   <span data-ttu-id="a6857-198">SqlMetal 嘗試擷取呼叫本身的預存程序。</span><span class="sxs-lookup"><span data-stu-id="a6857-198">SqlMetal tries to extract a stored procedure that calls itself.</span></span>  
  
-   <span data-ttu-id="a6857-199">預存程序、函式或檢視的巢狀層超過 32。</span><span class="sxs-lookup"><span data-stu-id="a6857-199">The nesting level of a stored procedure, function, or view exceeds 32.</span></span>  
  
     <span data-ttu-id="a6857-200">SqlMetal 會快取這個例外狀況並回報為警告。</span><span class="sxs-lookup"><span data-stu-id="a6857-200">SqlMetal catches this exception and reports it as a warning.</span></span>  
  
 <span data-ttu-id="a6857-201">若要指定輸入檔案名稱，請將名稱以輸入檔案加入命令列。</span><span class="sxs-lookup"><span data-stu-id="a6857-201">To specify an input file name, add the name to the command line as the input file.</span></span> <span data-ttu-id="a6857-202">不支援將檔案名稱包含在連接字串中 (使用 **/conn** 選項)。</span><span class="sxs-lookup"><span data-stu-id="a6857-202">Including the file name in the connection string (using the **/conn** option) is not supported.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a6857-203">範例</span><span class="sxs-lookup"><span data-stu-id="a6857-203">Examples</span></span>  
 <span data-ttu-id="a6857-204">產生 .dbml 檔，其中包含擷取的 SQL 中繼資料：</span><span class="sxs-lookup"><span data-stu-id="a6857-204">Generate a .dbml file that includes extracted SQL metadata:</span></span>  
  
 <span data-ttu-id="a6857-205">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span><span class="sxs-lookup"><span data-stu-id="a6857-205">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span></span>  
  
 <span data-ttu-id="a6857-206">產生 .dbml 檔，其中包括使用 SQL Server Express 從 .mdf 檔擷取的 SQL 中繼資料：</span><span class="sxs-lookup"><span data-stu-id="a6857-206">Generate a .dbml file that includes extracted SQL metadata from an .mdf file by using SQL Server Express:</span></span>  
  
 <span data-ttu-id="a6857-207">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span><span class="sxs-lookup"><span data-stu-id="a6857-207">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span></span>  
  
 <span data-ttu-id="a6857-208">產生 .dbml 檔，其中包括從 SQL Server Express 擷取的 SQL 中繼資料：</span><span class="sxs-lookup"><span data-stu-id="a6857-208">Generate a .dbml file that includes extracted SQL metadata from SQL Server Express:</span></span>  
  
 <span data-ttu-id="a6857-209">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span><span class="sxs-lookup"><span data-stu-id="a6857-209">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span></span>  
  
 <span data-ttu-id="a6857-210">從 .dbml 中繼資料檔產生原始程式碼：</span><span class="sxs-lookup"><span data-stu-id="a6857-210">Generate source code from a .dbml metadata file:</span></span>  
  
 <span data-ttu-id="a6857-211">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span><span class="sxs-lookup"><span data-stu-id="a6857-211">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span></span>  
  
 <span data-ttu-id="a6857-212">直接從 SQL 中繼資料產生原始程式碼：</span><span class="sxs-lookup"><span data-stu-id="a6857-212">Generate source code from SQL metadata directly:</span></span>  
  
 <span data-ttu-id="a6857-213">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span><span class="sxs-lookup"><span data-stu-id="a6857-213">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6857-214">當您使用 **/pluralize** 選項搭配 Northwind 範例資料庫時，請注意以下行為：</span><span class="sxs-lookup"><span data-stu-id="a6857-214">When you use the **/pluralize** option with the Northwind sample database, note the following behavior.</span></span> <span data-ttu-id="a6857-215">當 SqlMetal 提供資料表的資料列類型名稱時，資料表名稱會是單數。</span><span class="sxs-lookup"><span data-stu-id="a6857-215">When SqlMetal makes row-type names for tables, the table names are singular.</span></span> <span data-ttu-id="a6857-216">當它為資料表提供 <xref:System.Data.Linq.DataContext> 屬性時，資料表名稱會是複數。</span><span class="sxs-lookup"><span data-stu-id="a6857-216">When it makes <xref:System.Data.Linq.DataContext> properties for tables, the table names are plural.</span></span> <span data-ttu-id="a6857-217">碰巧的是，Northwind 範例資料庫中的資料表已經是複數。</span><span class="sxs-lookup"><span data-stu-id="a6857-217">Coincidentally, the tables in the Northwind sample database are already plural.</span></span> <span data-ttu-id="a6857-218">因此您不會看見該部分的運作情形。</span><span class="sxs-lookup"><span data-stu-id="a6857-218">Therefore, you do not see that part working.</span></span> <span data-ttu-id="a6857-219">雖然一般會將資料庫資料表的名稱設為單數，在 .NET 中仍然常會把集合名稱設為複數。</span><span class="sxs-lookup"><span data-stu-id="a6857-219">Although it is common practice to name database tables singular, it is also a common practice in .NET to name collections plural.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6857-220">請參閱</span><span class="sxs-lookup"><span data-stu-id="a6857-220">See Also</span></span>  
 [<span data-ttu-id="a6857-221">如何：以 Visual Basic 或 C# 產生物件模型</span><span class="sxs-lookup"><span data-stu-id="a6857-221">How to: Generate the Object Model in Visual Basic or C#</span></span>](../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)  
 [<span data-ttu-id="a6857-222">LINQ to SQL 中的程式碼產生</span><span class="sxs-lookup"><span data-stu-id="a6857-222">Code Generation in LINQ to SQL</span></span>](../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [<span data-ttu-id="a6857-223">外部對應</span><span class="sxs-lookup"><span data-stu-id="a6857-223">External Mapping</span></span>](../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
