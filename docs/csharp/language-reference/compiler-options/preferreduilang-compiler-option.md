---
title: "-preferreduilang (C# 編譯器選項)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /preferreduilang
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4fcf075dd951d733d294a62de98365c77b16a51d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="00891-102">-preferreduilang (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="00891-102">-preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="00891-103">使用 `-preferreduilang` 編譯器選項，您就可以指定 C# 編譯器顯示輸出的語言，例如錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="00891-103">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00891-104">語法</span><span class="sxs-lookup"><span data-stu-id="00891-104">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="00891-105">引數</span><span class="sxs-lookup"><span data-stu-id="00891-105">Arguments</span></span>  
 `language`  
 <span data-ttu-id="00891-106">編譯器輸出所用語言的[語言名稱](https://msdn.microsoft.com/library/windows/desktop/dd318696(v=vs.85).aspx)。</span><span class="sxs-lookup"><span data-stu-id="00891-106">The [language name](https://msdn.microsoft.com/library/windows/desktop/dd318696(v=vs.85).aspx) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00891-107">備註</span><span class="sxs-lookup"><span data-stu-id="00891-107">Remarks</span></span>  
 <span data-ttu-id="00891-108">您可以使用 `-preferreduilang` 編譯器選項指定 C# 編譯器要用於錯誤訊息和其他命令列輸出的語言。</span><span class="sxs-lookup"><span data-stu-id="00891-108">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="00891-109">如果尚未安裝此語言的語言套件，則會改用作業系統的語言設定，而且不會回報錯誤。</span><span class="sxs-lookup"><span data-stu-id="00891-109">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="00891-110">需求</span><span class="sxs-lookup"><span data-stu-id="00891-110">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00891-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="00891-111">See Also</span></span>  
 [<span data-ttu-id="00891-112">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="00891-112">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
