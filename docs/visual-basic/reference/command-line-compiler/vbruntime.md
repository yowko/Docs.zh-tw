---
title: -vbruntime
ms.date: 03/13/2018
f1_keywords:
- vbruntime
- -vbruntime
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
ms.openlocfilehash: 46d4b095d4a2bf9aac9124d5d4b2a09adb347ba1
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085057"
---
# <a name="-vbruntime"></a><span data-ttu-id="76049-102">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="76049-102">-vbruntime</span></span>

<span data-ttu-id="76049-103">指定編譯器在編譯時不應使用 Visual Basic 執行階段程式庫的參考，或應使用特定執行階段程式庫的參考。</span><span class="sxs-lookup"><span data-stu-id="76049-103">Specifies that the compiler should compile without a reference to the Visual Basic Runtime Library, or with a reference to a specific runtime library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76049-104">語法</span><span class="sxs-lookup"><span data-stu-id="76049-104">Syntax</span></span>  
  
```console  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a><span data-ttu-id="76049-105">引數</span><span class="sxs-lookup"><span data-stu-id="76049-105">Arguments</span></span>  

 \-  
 <span data-ttu-id="76049-106">不使用 Visual Basic 執行時間程式庫的參考編譯。</span><span class="sxs-lookup"><span data-stu-id="76049-106">Compile without a reference to the Visual Basic Runtime Library.</span></span>  
  
 \+  
 <span data-ttu-id="76049-107">使用預設的 Visual Basic 執行時間程式庫的參考編譯。</span><span class="sxs-lookup"><span data-stu-id="76049-107">Compile with a reference to the default Visual Basic Runtime Library.</span></span>  
  
 \*  
 <span data-ttu-id="76049-108">在不參考 Visual Basic 執行時間程式庫的情況下進行編譯，並將 Visual Basic 執行時間程式庫中的核心功能內嵌至元件。</span><span class="sxs-lookup"><span data-stu-id="76049-108">Compile without a reference to the Visual Basic Runtime Library, and embed core functionality from the Visual Basic Runtime Library into the assembly.</span></span>  
  
 `path`  
 <span data-ttu-id="76049-109">使用指定之程式庫 (DLL) 的參考編譯。</span><span class="sxs-lookup"><span data-stu-id="76049-109">Compile with a reference to the specified library (DLL).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76049-110">備註</span><span class="sxs-lookup"><span data-stu-id="76049-110">Remarks</span></span>  

 <span data-ttu-id="76049-111">`-vbruntime`編譯器選項可讓您指定編譯器在沒有 Visual Basic 執行時間程式庫的參考下進行編譯。</span><span class="sxs-lookup"><span data-stu-id="76049-111">The `-vbruntime` compiler option enables you to specify that the compiler should compile without a reference to the Visual Basic Runtime Library.</span></span> <span data-ttu-id="76049-112">如果您編譯時沒有 Visual Basic 執行時間程式庫的參考，則會在產生 Visual Basic 執行時間協助程式呼叫的程式碼或語言結構上記錄錯誤或警告。</span><span class="sxs-lookup"><span data-stu-id="76049-112">If you compile without a reference to the Visual Basic Runtime Library, errors or warnings are logged on code or language constructs that generate a call to a Visual Basic runtime helper.</span></span> <span data-ttu-id="76049-113"> (*Visual Basic 運行* 時間協助程式是在 Microsoft.VisualBasic.dll 中定義的函式，該函式會在執行時間呼叫以執行特定語言語義。 ) </span><span class="sxs-lookup"><span data-stu-id="76049-113">(A *Visual Basic runtime helper* is a function defined in Microsoft.VisualBasic.dll that is called at runtime to execute a specific language semantic.)</span></span>  
  
 <span data-ttu-id="76049-114">`-vbruntime+`如果未指定任何參數，則選項會產生相同的行為 `-vbruntime` 。</span><span class="sxs-lookup"><span data-stu-id="76049-114">The `-vbruntime+` option produces the same behavior that occurs if no `-vbruntime` switch is specified.</span></span> <span data-ttu-id="76049-115">您可以使用 `-vbruntime+` 選項來覆寫先前的 `-vbruntime` 參數。</span><span class="sxs-lookup"><span data-stu-id="76049-115">You can use the `-vbruntime+` option to override previous `-vbruntime` switches.</span></span>  
  
 <span data-ttu-id="76049-116">`My`當您使用或選項時，類型的大部分物件都無法使用 `-vbruntime-` `-vbruntime:path` 。</span><span class="sxs-lookup"><span data-stu-id="76049-116">Most objects of the `My` type are unavailable when you use the `-vbruntime-` or `-vbruntime:path` options.</span></span>  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a><span data-ttu-id="76049-117">內嵌 Visual Basic Runtime 核心功能</span><span class="sxs-lookup"><span data-stu-id="76049-117">Embedding Visual Basic Runtime core functionality</span></span>  

 <span data-ttu-id="76049-118">此 `-vbruntime*` 選項可讓您編譯而不需要執行時間程式庫的參考。</span><span class="sxs-lookup"><span data-stu-id="76049-118">The `-vbruntime*` option enables you to compile without a reference to a runtime library.</span></span> <span data-ttu-id="76049-119">相反地，Visual Basic 執行時間程式庫中的核心功能內嵌于使用者元件中。</span><span class="sxs-lookup"><span data-stu-id="76049-119">Instead, core functionality from the Visual Basic Runtime Library is embedded in the user assembly.</span></span> <span data-ttu-id="76049-120">如果您的應用程式是在不包含 Visual Basic 執行時間的平臺上執行，您可以使用此選項。</span><span class="sxs-lookup"><span data-stu-id="76049-120">You can use this option if your application runs on platforms that do not contain the Visual Basic runtime.</span></span>  
  
 <span data-ttu-id="76049-121">下列是內嵌的執行時間成員：</span><span class="sxs-lookup"><span data-stu-id="76049-121">The following runtime members are embedded:</span></span>  
  
- <span data-ttu-id="76049-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions> 類別</span><span class="sxs-lookup"><span data-stu-id="76049-122"><xref:Microsoft.VisualBasic.CompilerServices.Conversions> class</span></span>  
  
- <span data-ttu-id="76049-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> 方法</span><span class="sxs-lookup"><span data-stu-id="76049-123"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> method</span></span>  
  
- <span data-ttu-id="76049-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> 方法</span><span class="sxs-lookup"><span data-stu-id="76049-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> method</span></span>  
  
- <span data-ttu-id="76049-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> 方法</span><span class="sxs-lookup"><span data-stu-id="76049-125"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> method</span></span>  
  
- <span data-ttu-id="76049-126"><xref:Microsoft.VisualBasic.Constants.vbBack> 不斷</span><span class="sxs-lookup"><span data-stu-id="76049-126"><xref:Microsoft.VisualBasic.Constants.vbBack> constant</span></span>  
  
- <span data-ttu-id="76049-127"><xref:Microsoft.VisualBasic.Constants.vbCr> 不斷</span><span class="sxs-lookup"><span data-stu-id="76049-127"><xref:Microsoft.VisualBasic.Constants.vbCr> constant</span></span>  
  
- <span data-ttu-id="76049-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf> 不斷</span><span class="sxs-lookup"><span data-stu-id="76049-128"><xref:Microsoft.VisualBasic.Constants.vbCrLf> constant</span></span>  
  
- <span data-ttu-id="76049-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> 不斷</span><span class="sxs-lookup"><span data-stu-id="76049-129"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> constant</span></span>  
  
- <span data-ttu-id="76049-130"><xref:Microsoft.VisualBasic.Constants.vbLf> 不斷</span><span class="sxs-lookup"><span data-stu-id="76049-130"><xref:Microsoft.VisualBasic.Constants.vbLf> constant</span></span>  
  
- <span data-ttu-id="76049-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine> 不斷</span><span class="sxs-lookup"><span data-stu-id="76049-131"><xref:Microsoft.VisualBasic.Constants.vbNewLine> constant</span></span>  
  
- <span data-ttu-id="76049-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar> 不斷</span><span class="sxs-lookup"><span data-stu-id="76049-132"><xref:Microsoft.VisualBasic.Constants.vbNullChar> constant</span></span>  
  
- <span data-ttu-id="76049-133"><xref:Microsoft.VisualBasic.Constants.vbNullString> 不斷</span><span class="sxs-lookup"><span data-stu-id="76049-133"><xref:Microsoft.VisualBasic.Constants.vbNullString> constant</span></span>  
  
- <span data-ttu-id="76049-134"><xref:Microsoft.VisualBasic.Constants.vbTab> 不斷</span><span class="sxs-lookup"><span data-stu-id="76049-134"><xref:Microsoft.VisualBasic.Constants.vbTab> constant</span></span>  
  
- <span data-ttu-id="76049-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> 不斷</span><span class="sxs-lookup"><span data-stu-id="76049-135"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> constant</span></span>  
  
- <span data-ttu-id="76049-136">類型的部分物件 `My`</span><span class="sxs-lookup"><span data-stu-id="76049-136">Some objects of the `My` type</span></span>  
  
 <span data-ttu-id="76049-137">如果您使用選項進行編譯， `-vbruntime*` 而您的程式碼參考的 Visual Basic 執行時間程式庫中未以核心功能內嵌的成員，則編譯器會傳回指出該成員無法使用的錯誤。</span><span class="sxs-lookup"><span data-stu-id="76049-137">If you compile using the `-vbruntime*` option and your code references a member from the Visual Basic Runtime Library that is not embedded with the core functionality, the compiler returns an error that indicates that the member is not available.</span></span>  
  
## <a name="referencing-a-specified-library"></a><span data-ttu-id="76049-138">參考指定的程式庫</span><span class="sxs-lookup"><span data-stu-id="76049-138">Referencing a specified library</span></span>  

 <span data-ttu-id="76049-139">您可以使用 `path` 引數，以自訂執行時間程式庫的參考進行編譯，而不是預設的 Visual Basic 執行時間程式庫。</span><span class="sxs-lookup"><span data-stu-id="76049-139">You can use the `path` argument to compile with a reference to a custom runtime library instead of the default Visual Basic Runtime Library.</span></span>  
  
 <span data-ttu-id="76049-140">如果引數的值 `path` 是 DLL 的完整路徑，則編譯器會使用該檔案做為執行時間程式庫。</span><span class="sxs-lookup"><span data-stu-id="76049-140">If the value for the `path` argument is a fully qualified path to a DLL, the compiler will use that file as the runtime library.</span></span> <span data-ttu-id="76049-141">如果引數的值 `path` 不是 DLL 的完整路徑，Visual Basic 編譯器會先在目前的資料夾中搜尋識別的 dll。</span><span class="sxs-lookup"><span data-stu-id="76049-141">If the value for the `path` argument is not a fully qualified path to a DLL, the Visual Basic compiler will search for the identified DLL in the current folder first.</span></span> <span data-ttu-id="76049-142">然後，它會在您使用 [-sdkpath](sdkpath.md) 編譯器選項指定的路徑中進行搜尋。</span><span class="sxs-lookup"><span data-stu-id="76049-142">It will then search in the path that you have specified by using the [-sdkpath](sdkpath.md) compiler option.</span></span> <span data-ttu-id="76049-143">如果 `-sdkpath` 未使用編譯器選項，則編譯器會在 .NET Framework 資料夾 () 中搜尋識別的 DLL `%systemroot%\Microsoft.NET\Framework\versionNumber` 。</span><span class="sxs-lookup"><span data-stu-id="76049-143">If the `-sdkpath` compiler option is not used, the compiler will search for the identified DLL in the .NET Framework folder (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span></span>  
  
## <a name="example"></a><span data-ttu-id="76049-144">範例</span><span class="sxs-lookup"><span data-stu-id="76049-144">Example</span></span>  

 <span data-ttu-id="76049-145">下列範例顯示如何使用 `-vbruntime` 選項，以自訂程式庫的參考進行編譯。</span><span class="sxs-lookup"><span data-stu-id="76049-145">The following example shows how to use the `-vbruntime` option to compile with a reference to a custom library.</span></span>  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="76049-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76049-146">See also</span></span>

- [<span data-ttu-id="76049-147">Visual Basic Core – Visual Studio 2010 SP1 中的新編譯模式</span><span class="sxs-lookup"><span data-stu-id="76049-147">Visual Basic Core – New compilation mode in Visual Studio 2010 SP1</span></span>](https://devblogs.microsoft.com/vbteam/vb-core-new-compilation-mode-in-visual-studio-2010-sp1/)
- [<span data-ttu-id="76049-148">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="76049-148">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="76049-149">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="76049-149">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="76049-150">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="76049-150">-sdkpath</span></span>](sdkpath.md)
