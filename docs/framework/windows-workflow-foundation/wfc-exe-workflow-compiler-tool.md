---
title: 'Wfc.exe (工作流程命令列編譯器工具) '
description: 瞭解 wfc.exe，工作流程命令列編譯器工具。
ms.date: 10/10/2020
helpviewer_keywords:
- wfc [Workflow]
- compiler tool
- wfc.exe
- Workflow, compilation
- Workflow, XOML files
- Workflow, wcf
ms.openlocfilehash: cf89962014584adf098118044b063b38b29160b7
ms.sourcegitcommit: a6bd4cad438fe479cbd112eae10f2cd449f06e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2020
ms.locfileid: "91844598"
---
# <a name="wfcexe-workflow-command-line-compiler-tool"></a><span data-ttu-id="62e21-103">wfc.exe (工作流程命令列編譯器工具) </span><span class="sxs-lookup"><span data-stu-id="62e21-103">wfc.exe (Workflow Command-line Compiler Tool)</span></span>
> [!NOTE]
> <span data-ttu-id="62e21-104">此資料討論已被汰換的類型及命名空間。</span><span class="sxs-lookup"><span data-stu-id="62e21-104">This material discusses types and namespaces that are obsolete.</span></span>

<span data-ttu-id="62e21-105">wfc.exe 工作流程命令列編譯器工具適用于副檔名為 *xoml* () 的舊工作流程標記檔案。</span><span class="sxs-lookup"><span data-stu-id="62e21-105">The wfc.exe workflow command-line compiler tool works with old workflow markup files that have the file extension *.xoml* (obsoleted).</span></span>

## <a name="compilation-process"></a><span data-ttu-id="62e21-106">編譯流程</span><span class="sxs-lookup"><span data-stu-id="62e21-106">Compilation process</span></span>

<span data-ttu-id="62e21-107">編譯工作流程時，編譯處理程序會執行下列程序：</span><span class="sxs-lookup"><span data-stu-id="62e21-107">When workflows are compiled, the following procedures are performed as part of the compilation process:</span></span>

- <span data-ttu-id="62e21-108">執行驗證，以根據工作流程活動為自己設定的規則確認這些活動是有效的。</span><span class="sxs-lookup"><span data-stu-id="62e21-108">Validation is performed to ensure that the workflow activities validate based on the rules that the activities have set for themselves.</span></span> <span data-ttu-id="62e21-109">如果驗證錯誤，則編譯器會傳回錯誤清單。</span><span class="sxs-lookup"><span data-stu-id="62e21-109">If there are validation errors, the compiler returns a list of the errors.</span></span>  
- <span data-ttu-id="62e21-110">從輸入編譯器的標記定義產生部分類別。</span><span class="sxs-lookup"><span data-stu-id="62e21-110">A partial class is generated from the markup definition that is input into the compiler.</span></span>  

- <span data-ttu-id="62e21-111">產生程式碼來協助活動的執行階段執行。</span><span class="sxs-lookup"><span data-stu-id="62e21-111">Code is generated to help with the run-time execution of the activities.</span></span> <span data-ttu-id="62e21-112">產生事件訂閱來協助活動知道它們所包含的活動何時完成執行。</span><span class="sxs-lookup"><span data-stu-id="62e21-112">Event subscriptions are generated, which help activities know when the activities they contain are finished executing.</span></span>  
- <span data-ttu-id="62e21-113">從標記檔產生的部分類別和從程式碼檔產生的部分類別會進入 .NET Framework C# 或 Visual Basic 編譯器。</span><span class="sxs-lookup"><span data-stu-id="62e21-113">The partial classes generated from the markup file and the partial classes from the code file are entered into the .NET Framework C# or Visual Basic compiler.</span></span> <span data-ttu-id="62e21-114">這個程序的輸出為 .NET 組件 WorkflowSample.dll。</span><span class="sxs-lookup"><span data-stu-id="62e21-114">The output of this process is the .NET assembly, WorkflowSample.dll.</span></span> <span data-ttu-id="62e21-115">您可以部署這個組件來執行工作流程。</span><span class="sxs-lookup"><span data-stu-id="62e21-115">This can be deployed to run the workflow.</span></span>

### <a name="compiler-options"></a><span data-ttu-id="62e21-116">編譯器選項</span><span class="sxs-lookup"><span data-stu-id="62e21-116">Compiler options</span></span>

<span data-ttu-id="62e21-117">本節顯示 wfc.exe 工作流程命令列編譯器的選項。</span><span class="sxs-lookup"><span data-stu-id="62e21-117">This section shows the options for the wfc.exe workflow command-line compiler.</span></span>

```output
    Microsoft (R) Windows Workflow Compiler version 3.0.0.0
    Copyright (C) Microsoft Corporation 2005. All rights reserved.

                      Windows Workflow Compiler Options

    wfc.exe <Xoml file list> /target:assembly [<vb/cs file list>] [/language:...]
            [/out:...] [/reference:...] [/library:...] [/debug...] [/nocode...]
             [/checktypes...] [/resource:<resource info>]

                            - OUTPUT FILE -
    /out:<file>             Output file name
    /target:assembly        Build a Windows Workflow assembly (default).
                            Short form: /t:assembly
    /target:exe             Build a Windows Workflow application.
                            Short form: /t:exe
    /delaysign[+|-]         Delay-sign the assembly using only the public portion
                            of the strong name key.
    /keyfile:<file>         Specifies a strong name key file.
    /keycontainer:<string>  Specifies a strong name key container.

                            - INPUT FILES -
    <Xoml file list>        Xoml source file name(s).
    <vb/cs file list>       Code-beside file name(s).
    /reference:<file list>  Reference metadata from the specified assembly file(s).
                            Short form is '/r:'.
    /library:<path list>    Set of directories where to lookup for the references.
                            Short form is '/lib:'.
    /resource:<resinfo>     Embed the specified resource. Short form is '/res:'.
                            resinfo format is <file>[,<name>[,public|private]].

    Rules and freeform layout files must be embedded as assembly resources.
    The resource name is constructed by using the namespace and type name
    of the activity. For example, an activity named "MyActivity" in namespace
    "WFProject" would require resource names "WFProject.MyActivity.rules"
    and/or "WFProject.MyActivity.layout".

                            - CODE GENERATION -
    /debug[+|-]             Emit full debugging information. The default is '+'.
    /nocode[+|-]            Disallow code-beside model.
                            The default is '-'. Short form is '/nc:'.
    /checktypes[+|-]        Check for permitted types in wfc.exe.config file.
                            The default is '-'. Short form is '/ct:'.

                            - LANGUAGE -
    /language:[cs|vb]       The language to use for the generated class.
                            The default is 'CS' (C#). Short form is '/l:'.
    /rootnamespace:<string> Specifies the root Namespace for all type declarations.
                            Valid only for 'VB' (Visual Basic) language.
                            Short form is '/rns:'.

                            - MISCELLANEOUS -
    /help                   Display this usage message. Short form is '/?'.
    /nologo                 Suppress compiler copyright message. Short form is '/n'.

    /nowarn                 Ignore compiler warnings. Short form is '/w'.
```

## <a name="remarks"></a><span data-ttu-id="62e21-118">備註</span><span class="sxs-lookup"><span data-stu-id="62e21-118">Remarks</span></span>
> [!NOTE]
> <span data-ttu-id="62e21-119">此資料討論已被汰換的類型及命名空間。</span><span class="sxs-lookup"><span data-stu-id="62e21-119">This material discusses types and namespaces that are obsolete.</span></span>

<span data-ttu-id="62e21-120">授權型別的清單通常會在 *wfc.exe.config* 檔案中定義。</span><span class="sxs-lookup"><span data-stu-id="62e21-120">A list of authorized types is usually defined in the *wfc.exe.config* file.</span></span> <span data-ttu-id="62e21-121">在工作流程編譯的驗證階段期間，如果工作流程來源文件或隨附規則檔案直接參考任何未出現在授權類型清單中的 .NET Framework 類型，則會拒絕該工作流程來源文件。</span><span class="sxs-lookup"><span data-stu-id="62e21-121">During the validation phase of workflow compilation, a workflow source document is rejected if it or the companion rules file directly references any .NET Framework types not present in a list of authorized types.</span></span> <span data-ttu-id="62e21-122">授權型別的清單是 XML 檔，其中每個專案都指出 `Assembly` 、、 `Namespace` `TypeName` 和授權的 { `True`&#124;`False` } 指標。</span><span class="sxs-lookup"><span data-stu-id="62e21-122">The list of authorized types is an XML document where each entry indicates an `Assembly`, a `Namespace`, a `TypeName`, and an Authorized {`True`&#124;`False`} indicator.</span></span> <span data-ttu-id="62e21-123">`AuthorizedType` 對應至清單中的專案。</span><span class="sxs-lookup"><span data-stu-id="62e21-123">`AuthorizedType` corresponds to an entry in the list.</span></span> <span data-ttu-id="62e21-124">允許用來包含或排除完整命名空間的萬用字元標記法。</span><span class="sxs-lookup"><span data-stu-id="62e21-124">Wildcard character designations, which can be used to include or exclude complete namespaces, are allowed.</span></span> <span data-ttu-id="62e21-125">例如， `Type="System.*"` 包含中的所有類型 <xref:System> ，包括子命名空間中包含的類型。</span><span class="sxs-lookup"><span data-stu-id="62e21-125">For example, `Type="System.*"` includes all types in <xref:System>, including types contained in child namespaces.</span></span>
  
<span data-ttu-id="62e21-126">授權類型清單的使用是由選項所控制 <xref:System.Workflow.ComponentModel.Compiler.WorkflowCompiler> `'/checktypes'` 。</span><span class="sxs-lookup"><span data-stu-id="62e21-126">The use of a list of authorized types is controlled by the <xref:System.Workflow.ComponentModel.Compiler.WorkflowCompiler> option `'/checktypes'`.</span></span>

```xml  
<configuration>  
  <System.Workflow.ComponentModel.WorkflowCompiler>
    <authorizedTypes>
      <targetFx version="v4.0">
        ...
        <authorizedType Assembly="System, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" Namespace="System*" TypeName="*" Authorized="True"/>
        ...
      </targetFx>
    </authorizedTypes>
  </System.Workflow.ComponentModel.WorkflowCompiler>  
</configuration>  
```

> [!WARNING]
> <span data-ttu-id="62e21-127">當 `Type="System.*"` 類型存在時，可以包含其他非預期的類型（例如 `Type="System.Configuration"` ）進行編譯。</span><span class="sxs-lookup"><span data-stu-id="62e21-127">When `Type="System.*"` type is present, it's possible to include other unintended types, such as `Type="System.Configuration"`, for compilation.</span></span> <span data-ttu-id="62e21-128">您應該小心並檢查每一個。</span><span class="sxs-lookup"><span data-stu-id="62e21-128">You should be cautious and review each one.</span></span> <span data-ttu-id="62e21-129">對於任何應該限制的類型，請務必將設定 `Authorized` 為 `False` 。</span><span class="sxs-lookup"><span data-stu-id="62e21-129">For any type that should be restricted, be sure to set `Authorized` to `False`.</span></span>

## <a name="see-also"></a><span data-ttu-id="62e21-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="62e21-130">See also</span></span>

- [<span data-ttu-id="62e21-131">AuthorizedType 類別</span><span class="sxs-lookup"><span data-stu-id="62e21-131">AuthorizedType class</span></span>](xref:System.Workflow.ComponentModel.Compiler.AuthorizedType)
