---
title: Mgmtclassgen.exe (管理強類型類別產生器)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CIM types
- Management Strongly Typed Class Generator
- WMI class
- Mgmtclassgen.exe
- early-bound managed classes
ms.assetid: 02ce6699-49b5-4a0b-b0d5-1003c491232e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b40cb5d5d629ea7a3cb019be42b42a1072572311
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044377"
---
# <a name="mgmtclassgenexe-management-strongly-typed-class-generator"></a><span data-ttu-id="edbda-102">Mgmtclassgen.exe (管理強類型類別產生器)</span><span class="sxs-lookup"><span data-stu-id="edbda-102">Mgmtclassgen.exe (Management Strongly Typed Class Generator)</span></span>
<span data-ttu-id="edbda-103">[管理強類型類別產生器] 工具可快速地為指定的 Windows Management Instrumentation (WMI) 類別產生早期繫結 Managed 類別。</span><span class="sxs-lookup"><span data-stu-id="edbda-103">The Management Strongly Typed Class Generator tool enables you to quickly generate an early-bound managed class for a specified Windows Management Instrumentation (WMI) class.</span></span> <span data-ttu-id="edbda-104">產生的類別會將為存取 WMI 類別之執行個體所撰寫的程式碼加以簡化。</span><span class="sxs-lookup"><span data-stu-id="edbda-104">The generated class simplifies the code you must write to access an instance of the WMI class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edbda-105">語法</span><span class="sxs-lookup"><span data-stu-id="edbda-105">Syntax</span></span>  
  
```console  
mgmtclassgen   
WMIClass [options]   
```  
  
|<span data-ttu-id="edbda-106">引數</span><span class="sxs-lookup"><span data-stu-id="edbda-106">Argument</span></span>|<span data-ttu-id="edbda-107">描述</span><span class="sxs-lookup"><span data-stu-id="edbda-107">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="edbda-108">*WMIClass*</span><span class="sxs-lookup"><span data-stu-id="edbda-108">*WMIClass*</span></span>|<span data-ttu-id="edbda-109">要產生早期繫結 Managed 類別的 Windows Management Instrumentation 類別。</span><span class="sxs-lookup"><span data-stu-id="edbda-109">The Windows Management Instrumentation class for which to generate an early-bound managed class.</span></span>|  
  
|<span data-ttu-id="edbda-110">選項</span><span class="sxs-lookup"><span data-stu-id="edbda-110">Option</span></span>|<span data-ttu-id="edbda-111">說明</span><span class="sxs-lookup"><span data-stu-id="edbda-111">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="edbda-112">**/l**  *language*</span><span class="sxs-lookup"><span data-stu-id="edbda-112">**/l**  *language*</span></span>|<span data-ttu-id="edbda-113">指定要用來產生早期繫結 Managed 類別的語言。</span><span class="sxs-lookup"><span data-stu-id="edbda-113">Specifies the language in which to generate the early-bound managed class.</span></span> <span data-ttu-id="edbda-114">您可以指定 **CS** (C#，預設)、**VB** (Visual Basic)、**MC** (C++) 或 **JS** (JScript) 作為語言引數。</span><span class="sxs-lookup"><span data-stu-id="edbda-114">You can specify **CS** (C#; default), **VB** (Visual Basic),  **MC** (C++), or **JS** (JScript) as the language argument.</span></span>|  
|<span data-ttu-id="edbda-115">**/m**  <電腦></span><span class="sxs-lookup"><span data-stu-id="edbda-115">**/m**  *machine*</span></span>|<span data-ttu-id="edbda-116">指定要連接的電腦，其中內含 WMI 類別。</span><span class="sxs-lookup"><span data-stu-id="edbda-116">Specifies the computer to connect to, where the WMI class resides.</span></span> <span data-ttu-id="edbda-117">預設為本機電腦。</span><span class="sxs-lookup"><span data-stu-id="edbda-117">The default is the local computer.</span></span>|  
|<span data-ttu-id="edbda-118">**/n**  *path*</span><span class="sxs-lookup"><span data-stu-id="edbda-118">**/n**  *path*</span></span>|<span data-ttu-id="edbda-119">指定包含 WMI 類別之 WMI 命名空間的路徑。</span><span class="sxs-lookup"><span data-stu-id="edbda-119">Specifies the path to the WMI namespace that contains the WMI class.</span></span> <span data-ttu-id="edbda-120">如果沒有指定這個選項，則工具預設會產生 **Root\cimv2** 命名空間之 *WMIClass* 的程式碼。</span><span class="sxs-lookup"><span data-stu-id="edbda-120">If you do not specify this option, the tool generates code for *WMIClass* in the default **Root\cimv2** namespace.</span></span>|  
|<span data-ttu-id="edbda-121">**/o**  <類別命名空間></span><span class="sxs-lookup"><span data-stu-id="edbda-121">**/o**  *classnamespace*</span></span>|<span data-ttu-id="edbda-122">指定要產生 Managed 程式碼類別的 .NET 命名空間。</span><span class="sxs-lookup"><span data-stu-id="edbda-122">Specifies the .NET namespace in which to generate the managed code class.</span></span> <span data-ttu-id="edbda-123">如果沒有指定這個選項，則工具會產生使用 WMI 命名空間和結構描述前置詞的命名空間。</span><span class="sxs-lookup"><span data-stu-id="edbda-123">If you do not specify this option, the tool generates the namespace using the WMI namespace and the schema prefix.</span></span> <span data-ttu-id="edbda-124">結構描述前置詞是位在底線字元前之類別名稱的一部分。</span><span class="sxs-lookup"><span data-stu-id="edbda-124">The schema prefix is the part of the class name preceding the underscore character.</span></span> <span data-ttu-id="edbda-125">例如，針對 **Root\cimv2** 命名空間中的 **Win32_OperatingSystem** 類別，工具會在 **ROOT.CIMV2.Win32** 中產生類別。</span><span class="sxs-lookup"><span data-stu-id="edbda-125">For example, for the **Win32_OperatingSystem** class in the **Root\cimv2** namespace, the tool would generate the class in **ROOT.CIMV2.Win32**.</span></span>|  
|<span data-ttu-id="edbda-126">**/p**  <檔案路徑></span><span class="sxs-lookup"><span data-stu-id="edbda-126">**/p**  *filepath*</span></span>|<span data-ttu-id="edbda-127">指定用來儲存所產生之程式碼的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="edbda-127">Specifies the path to the file in which to save the generated code.</span></span> <span data-ttu-id="edbda-128">如果沒有指定這個選項，工具會將檔案建立在目前的目錄下。</span><span class="sxs-lookup"><span data-stu-id="edbda-128">If you do not specify this option, the tool creates the file in the current directory.</span></span> <span data-ttu-id="edbda-129">工具會使用 *WMIClass* 引數來為其產生類別的類別和檔案命名。</span><span class="sxs-lookup"><span data-stu-id="edbda-129">It names the class and file in which it generates the class using the *WMIClass* argument.</span></span> <span data-ttu-id="edbda-130">類別和檔案的名稱和 *WMIClass.* 的名稱一樣。</span><span class="sxs-lookup"><span data-stu-id="edbda-130">The name of the class and the file are the same as the name of the *WMIClass.*</span></span> <span data-ttu-id="edbda-131">如果 *WMIClass* 內含一個底線字元，工具會使用底線字元之後的類別名稱部分。</span><span class="sxs-lookup"><span data-stu-id="edbda-131">If *WMIClass* contains an underscore character, the tool uses the part of the class name following the underscore character.</span></span> <span data-ttu-id="edbda-132">例如，如果 *WMIClass* 名稱的格式為 **Win32_LogicalDisk**，則產生的類別和檔案將會命名為 "logicaldisk"。</span><span class="sxs-lookup"><span data-stu-id="edbda-132">For example, if the *WMIClass* name is in the format **Win32_LogicalDisk**, the generated class and file is named "logicaldisk".</span></span> <span data-ttu-id="edbda-133">如果檔案已存在，工具會覆寫現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="edbda-133">If a file already exists, the tool overwrites the existing file.</span></span>|  
|<span data-ttu-id="edbda-134">**/pw**  <密碼></span><span class="sxs-lookup"><span data-stu-id="edbda-134">**/pw**  *password*</span></span>|<span data-ttu-id="edbda-135">透過 **/m** 選項指定登入電腦時要使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="edbda-135">Specifies the password to use when logging on to a computer specified by the **/m** option.</span></span>|  
|<span data-ttu-id="edbda-136">**/u**  <使用者名稱></span><span class="sxs-lookup"><span data-stu-id="edbda-136">**/u**  *user name*</span></span>|<span data-ttu-id="edbda-137">透過 **/m** 選項指定登入電腦時要使用的使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="edbda-137">Specifies the user name to use when logging on to a computer specified by the **/m** option.</span></span>|  
|<span data-ttu-id="edbda-138">**/?**</span><span class="sxs-lookup"><span data-stu-id="edbda-138">**/?**</span></span>|<span data-ttu-id="edbda-139">顯示工具的命令語法和選項。</span><span class="sxs-lookup"><span data-stu-id="edbda-139">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="edbda-140">備註</span><span class="sxs-lookup"><span data-stu-id="edbda-140">Remarks</span></span>  
 <span data-ttu-id="edbda-141">Mgmtclassgen.exe 會使用 <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="edbda-141">Mgmtclassgen.exe uses the <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="edbda-142">因此，您可以使用任何自訂程式碼提供者來產生 Managed 語言 (不是 C#、Visual Basic 和 JScript) 的程式碼。</span><span class="sxs-lookup"><span data-stu-id="edbda-142">Therefore, you can use any custom code provider to generate code in managed languages other than C#, Visual Basic, and JScript.</span></span>  
  
 <span data-ttu-id="edbda-143">請注意，產生的類別會繫結至為其所產生的結構描述。</span><span class="sxs-lookup"><span data-stu-id="edbda-143">Note that generated classes are bound to the schema for which they are generated.</span></span> <span data-ttu-id="edbda-144">當基礎結構描述改變時，若要反映結構描述的這些改變就必須重新產生類別。</span><span class="sxs-lookup"><span data-stu-id="edbda-144">If the underlying schema changes, you must regenerate the class if you want it to reflect changes to the schema.</span></span>  
  
 <span data-ttu-id="edbda-145">下表顯示 WMI 通用訊息模型 (Common Information Model，CIM) 類型如何對應至所產生類別中的資料類型：</span><span class="sxs-lookup"><span data-stu-id="edbda-145">The following table shows how WMI Common Information Model (CIM) types map to data types in a generated class:</span></span>  
  
|<span data-ttu-id="edbda-146">CIM 類型</span><span class="sxs-lookup"><span data-stu-id="edbda-146">CIM type</span></span>|<span data-ttu-id="edbda-147">所產生之類別中的資料類型</span><span class="sxs-lookup"><span data-stu-id="edbda-147">Data type in the generated class</span></span>|  
|--------------|--------------------------------------|  
|<span data-ttu-id="edbda-148">CIM_SINT8</span><span class="sxs-lookup"><span data-stu-id="edbda-148">CIM_SINT8</span></span>|<span data-ttu-id="edbda-149">**SByte**</span><span class="sxs-lookup"><span data-stu-id="edbda-149">**SByte**</span></span>|  
|<span data-ttu-id="edbda-150">CIM_UINT8</span><span class="sxs-lookup"><span data-stu-id="edbda-150">CIM_UINT8</span></span>|<span data-ttu-id="edbda-151">**Byte**</span><span class="sxs-lookup"><span data-stu-id="edbda-151">**Byte**</span></span>|  
|<span data-ttu-id="edbda-152">CIM_SINT16</span><span class="sxs-lookup"><span data-stu-id="edbda-152">CIM_SINT16</span></span>|<span data-ttu-id="edbda-153">**Int16**</span><span class="sxs-lookup"><span data-stu-id="edbda-153">**Int16**</span></span>|  
|<span data-ttu-id="edbda-154">CIM_UINT16</span><span class="sxs-lookup"><span data-stu-id="edbda-154">CIM_UINT16</span></span>|<span data-ttu-id="edbda-155">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="edbda-155">**UInt16**</span></span>|  
|<span data-ttu-id="edbda-156">CIM_SINT32</span><span class="sxs-lookup"><span data-stu-id="edbda-156">CIM_SINT32</span></span>|<span data-ttu-id="edbda-157">**Int32**</span><span class="sxs-lookup"><span data-stu-id="edbda-157">**Int32**</span></span>|  
|<span data-ttu-id="edbda-158">SIM_UINT32</span><span class="sxs-lookup"><span data-stu-id="edbda-158">SIM_UINT32</span></span>|<span data-ttu-id="edbda-159">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="edbda-159">**UInt32**</span></span>|  
|<span data-ttu-id="edbda-160">CIM_SINT64</span><span class="sxs-lookup"><span data-stu-id="edbda-160">CIM_SINT64</span></span>|<span data-ttu-id="edbda-161">**Int64**</span><span class="sxs-lookup"><span data-stu-id="edbda-161">**Int64**</span></span>|  
|<span data-ttu-id="edbda-162">CIM_UINT64</span><span class="sxs-lookup"><span data-stu-id="edbda-162">CIM_UINT64</span></span>|<span data-ttu-id="edbda-163">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="edbda-163">**UInt64**</span></span>|  
|<span data-ttu-id="edbda-164">CIM_REAL32</span><span class="sxs-lookup"><span data-stu-id="edbda-164">CIM_REAL32</span></span>|<span data-ttu-id="edbda-165">**Single**</span><span class="sxs-lookup"><span data-stu-id="edbda-165">**Single**</span></span>|  
|<span data-ttu-id="edbda-166">CIM_REAL64</span><span class="sxs-lookup"><span data-stu-id="edbda-166">CIM_REAL64</span></span>|<span data-ttu-id="edbda-167">**Double**</span><span class="sxs-lookup"><span data-stu-id="edbda-167">**Double**</span></span>|  
|<span data-ttu-id="edbda-168">CIM_BOOLEAN</span><span class="sxs-lookup"><span data-stu-id="edbda-168">CIM_BOOLEAN</span></span>|<span data-ttu-id="edbda-169">**布林值**</span><span class="sxs-lookup"><span data-stu-id="edbda-169">**Boolean**</span></span>|  
|<span data-ttu-id="edbda-170">CIM_String</span><span class="sxs-lookup"><span data-stu-id="edbda-170">CIM_String</span></span>|<span data-ttu-id="edbda-171">**String**</span><span class="sxs-lookup"><span data-stu-id="edbda-171">**String**</span></span>|  
|<span data-ttu-id="edbda-172">CIM_DATETIME</span><span class="sxs-lookup"><span data-stu-id="edbda-172">CIM_DATETIME</span></span>|<span data-ttu-id="edbda-173">**DateTime** 或 **TimeSpan**</span><span class="sxs-lookup"><span data-stu-id="edbda-173">**DateTime** or **TimeSpan**</span></span>|  
|<span data-ttu-id="edbda-174">CIM_REFERENCE</span><span class="sxs-lookup"><span data-stu-id="edbda-174">CIM_REFERENCE</span></span>|<span data-ttu-id="edbda-175">**ManagementPath**</span><span class="sxs-lookup"><span data-stu-id="edbda-175">**ManagementPath**</span></span>|  
|<span data-ttu-id="edbda-176">CIM_CHAR16</span><span class="sxs-lookup"><span data-stu-id="edbda-176">CIM_CHAR16</span></span>|<span data-ttu-id="edbda-177">**Char**</span><span class="sxs-lookup"><span data-stu-id="edbda-177">**Char**</span></span>|  
|<span data-ttu-id="edbda-178">CIM_OBJECT</span><span class="sxs-lookup"><span data-stu-id="edbda-178">CIM_OBJECT</span></span>|<span data-ttu-id="edbda-179">**ManagementBaseObject**</span><span class="sxs-lookup"><span data-stu-id="edbda-179">**ManagementBaseObject**</span></span>|  
|<span data-ttu-id="edbda-180">CIM_IUNKNOWN</span><span class="sxs-lookup"><span data-stu-id="edbda-180">CIM_IUNKNOWN</span></span>|<span data-ttu-id="edbda-181">**物件**</span><span class="sxs-lookup"><span data-stu-id="edbda-181">**Object**</span></span>|  
|<span data-ttu-id="edbda-182">CIM_ARRAY</span><span class="sxs-lookup"><span data-stu-id="edbda-182">CIM_ARRAY</span></span>|<span data-ttu-id="edbda-183">上述物件的陣列</span><span class="sxs-lookup"><span data-stu-id="edbda-183">Array of the above mentioned objects</span></span>|  
  
 <span data-ttu-id="edbda-184">請注意下列在產生 WMI 類別時的行為：</span><span class="sxs-lookup"><span data-stu-id="edbda-184">Note the following behaviors when you generate a WMI class:</span></span>  
  
- <span data-ttu-id="edbda-185">標準公用屬性或方法有可能和現有屬性或方法的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="edbda-185">It is possible for a standard public property or method to have the same name as an existing property or method.</span></span> <span data-ttu-id="edbda-186">當此情況發生時，工具會變更在所產生之類別中屬性或方法的名稱以避免命名衝突。</span><span class="sxs-lookup"><span data-stu-id="edbda-186">If this occurs, the tool changes the name of the property or method in the generated class to avoid naming conflicts.</span></span>  
  
- <span data-ttu-id="edbda-187">所產生之類別中屬性或方法的名稱有可能是目標程式語言的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="edbda-187">It is possible for the name of a property or method in a generated class to be a keyword in the target programming language.</span></span> <span data-ttu-id="edbda-188">當此情況發生時，工具會變更在所產生之類別中屬性或方法的名稱以避免命名衝突。</span><span class="sxs-lookup"><span data-stu-id="edbda-188">If this occurs, the tool changes the name of the property or method in the generated class to avoid naming conflicts.</span></span>  
  
- <span data-ttu-id="edbda-189">在 WMI 中，限定詞為修飾詞，其中包含說明類別、執行個體、屬性或方法的資訊。</span><span class="sxs-lookup"><span data-stu-id="edbda-189">In WMI, qualifiers are modifiers that contain information to describe a class, instance, property, or method.</span></span> <span data-ttu-id="edbda-190">WMI 使用如 **Read**、**Write** 和 **Key** 等標準限定詞以說明產生之類別中的屬性。</span><span class="sxs-lookup"><span data-stu-id="edbda-190">WMI uses standard qualifiers such as **Read**, **Write**, and **Key** to describe a property in a generated class.</span></span> <span data-ttu-id="edbda-191">例如，以 **Read** 限定詞修飾的屬性只能以在所產生類別中的屬性 **get** 存取子來定義。</span><span class="sxs-lookup"><span data-stu-id="edbda-191">For example, a property that is modified with a **Read** qualifier is defined only with a property **get** accessor in the generated class.</span></span> <span data-ttu-id="edbda-192">因為以 **Read** 限定詞標記的屬性是做唯讀之用，不會定義 **set** 存取子。</span><span class="sxs-lookup"><span data-stu-id="edbda-192">Because a property marked with the **Read** qualifier is intended to be read-only, a **set** accessor is not defined.</span></span>  
  
- <span data-ttu-id="edbda-193">數值屬性可使用 **Values** 和 **ValueMaps** 限定詞加以修飾，表示屬性只能設定為指定的允許值。</span><span class="sxs-lookup"><span data-stu-id="edbda-193">A numeric property can be modified by the **Values** and **ValueMaps** qualifiers to indicate that the property can be set only to specified permissible values.</span></span> <span data-ttu-id="edbda-194">列舉是以這些 **Values** 和 **ValueMaps** 產生的，而屬性會對應到列舉。</span><span class="sxs-lookup"><span data-stu-id="edbda-194">An enumeration is generated with these **Values** and **ValueMaps** and the property is mapped to the enumeration.</span></span>  
  
- <span data-ttu-id="edbda-195">WMI 使用單一 (Singleton) 這個詞彙來說明只能有一個執行個體的類別。</span><span class="sxs-lookup"><span data-stu-id="edbda-195">The WMI uses the term singleton to describe a class that can have only one instance.</span></span> <span data-ttu-id="edbda-196">因此，單一 (Singleton) 類別的無參數建構函式會將類別初始化為該類別的唯一執行個體。</span><span class="sxs-lookup"><span data-stu-id="edbda-196">Therefore, the parameterless constructor for a singleton class will initialize the class to the only instance of the class.</span></span>  
  
- <span data-ttu-id="edbda-197">WMI 類別可以擁有物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="edbda-197">A WMI class can have properties that are objects.</span></span> <span data-ttu-id="edbda-198">當產生此類型之 WMI 類別的強類型類別時，應考慮產生此內嵌物件屬性類型的強類型類別。</span><span class="sxs-lookup"><span data-stu-id="edbda-198">When you generate a strongly-typed class for this type of WMI class, you should consider generating strongly-typed classes for the types of the embedded object properties.</span></span> <span data-ttu-id="edbda-199">這能讓您以強類型的方式存取內嵌物件。</span><span class="sxs-lookup"><span data-stu-id="edbda-199">This will allow you to access the embedded objects in a strongly-typed manner.</span></span> <span data-ttu-id="edbda-200">請注意，產生的程式碼可能無法偵測內嵌物件的類型。</span><span class="sxs-lookup"><span data-stu-id="edbda-200">Note that the generated code might not be able to detect the type of the embedded object.</span></span> <span data-ttu-id="edbda-201">在這個情況下，會在產生的程式碼中建立註解以告知您這個問題。</span><span class="sxs-lookup"><span data-stu-id="edbda-201">In this case, a comment will be created in the generated code to notify you of this issue.</span></span> <span data-ttu-id="edbda-202">接著，您可以將所產生程式碼的屬性類型修改為其他所產生類別的屬性類型。</span><span class="sxs-lookup"><span data-stu-id="edbda-202">You can then modify the generated code to type the property to the other generated class.</span></span>  
  
- <span data-ttu-id="edbda-203">WMI 中，CIM_DATETIME 資料類型的資料值可表示特定的日期和時間，或表示時間間隔。</span><span class="sxs-lookup"><span data-stu-id="edbda-203">In WMI, the data value of the CIM_DATETIME data type can represent either a specific date and time or a time interval.</span></span> <span data-ttu-id="edbda-204">如果資料值代表日期和時間，所產生類別中的資料類型就會是 **DateTime**。</span><span class="sxs-lookup"><span data-stu-id="edbda-204">If the data value represents a date and time, the data type in the generated class is **DateTime**.</span></span> <span data-ttu-id="edbda-205">如果資料值代表時間間隔，則所產生類別中的資料類型就會是 **TimeSpan**。</span><span class="sxs-lookup"><span data-stu-id="edbda-205">If the data value represents a time interval, the data type in the generated class is **TimeSpan**.</span></span>  
  
 <span data-ttu-id="edbda-206">您也可以使用 Visual Studio .NET 中的 Server Explorer Management Extension 來產生強類型類別。</span><span class="sxs-lookup"><span data-stu-id="edbda-206">You can alternately generate a strongly-typed class using the Server Explorer Management Extension in Visual Studio .NET.</span></span>  
  
 <span data-ttu-id="edbda-207">如需 WMI 的詳細資訊，請參閱 Platform SDK 說明文件中的 **Windows Management Instrumentation** 主題。</span><span class="sxs-lookup"><span data-stu-id="edbda-207">For more information about WMI, see the **Windows Management Instrumentation** topic in the Platform SDK documentation.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="edbda-208">範例</span><span class="sxs-lookup"><span data-stu-id="edbda-208">Examples</span></span>  
 <span data-ttu-id="edbda-209">下列命令會在 **Root\cimv2** 命名空間中產生 **Win32_LogicalDisk** WMI 類別的 Managed 類別 (以 C# 程式碼撰寫)。</span><span class="sxs-lookup"><span data-stu-id="edbda-209">The following command generates a managed class in C# code for the **Win32_LogicalDisk** WMI class in the **Root\cimv2** namespace.</span></span> <span data-ttu-id="edbda-210">工具會將 Managed 類別寫入 c:\disk.cs 的原始程式檔，放在 **ROOT.CIMV2.Win32** 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="edbda-210">The tool writes the managed class to the source file at c:\disk.cs in the **ROOT.CIMV2.Win32** namespace.</span></span>  
  
```console  
mgmtclassgen Win32_LogicalDisk /n root\cimv2 /l CS /p c:\disk.cs  
```  
  
 <span data-ttu-id="edbda-211">下列程式碼範例顯示如何以程式設計方式使用產生的類別。</span><span class="sxs-lookup"><span data-stu-id="edbda-211">The following code example shows how to use a generated class programmatically.</span></span> <span data-ttu-id="edbda-212">首先，列舉類別的執行個體並印出路徑。</span><span class="sxs-lookup"><span data-stu-id="edbda-212">First, an instance of the class is enumerated and the path is printed.</span></span> <span data-ttu-id="edbda-213">接下來，以 WMI 的執行個體建立要初始化所產生類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="edbda-213">Next, an instance of the generated class to be initialized is created with an instance of WMI.</span></span> <span data-ttu-id="edbda-214">`Process` 是為 **Win32_Process** 產生的類別，`LogicalDisk` 則是為 **Root\cimv2** 命名空間中 **Win32_LogicalDisk** 產生的類別。</span><span class="sxs-lookup"><span data-stu-id="edbda-214">`Process` is the class generated for **Win32_Process** and `LogicalDisk` is the class generated for **Win32_LogicalDisk** in the **Root\cimv2** namespace.</span></span>  
  
```vb  
Imports System  
Imports System.Management  
Imports ROOT.CIMV2.Win32  
  
Public Class App     
   Public Shared Sub Main()        
      ' Enumerate instances of the Win32_process.  
      ' Print the Name property of the instance.  
      Dim ps As Process     
      For Each ps In  Process.GetInstances()  
         Console.WriteLine(ps.Name)  
      Next ps  
  
      ' Initialize the instance of LogicalDisk with  
      ' the WMI instance pointing to logical drive d:.  
      Dim dskD As New LogicalDisk(New _  
         ManagementPath("win32_LogicalDisk.DeviceId=""d:"""))  
      Console.WriteLine(dskD.Caption)  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Management;  
using ROOT.CIMV2.Win32;  
  
public class App  
{  
   public static void Main()  
   {  
      // Enumerate instances of the Win32_process.  
      // Print the Name property of the instance.  
      foreach(Process ps in Process.GetInstances())  
      {  
         Console.WriteLine(ps.Name);  
      }  
  
      // Initialize the instance of LogicalDisk with  
      // the WMI instance pointing to logical drive d:.  
      LogicalDisk dskD = new LogicalDisk(new ManagementPath(  
        "win32_LogicalDisk.DeviceId=\"d:\""));  
      Console.WriteLine(dskD.Caption);  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="edbda-215">另請參閱</span><span class="sxs-lookup"><span data-stu-id="edbda-215">See also</span></span>

- <xref:System.Management>
- <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType>
- <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>
- [<span data-ttu-id="edbda-216">工具</span><span class="sxs-lookup"><span data-stu-id="edbda-216">Tools</span></span>](index.md)
- [<span data-ttu-id="edbda-217">命令提示字元</span><span class="sxs-lookup"><span data-stu-id="edbda-217">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
