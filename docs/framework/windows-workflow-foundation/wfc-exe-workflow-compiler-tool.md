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
# <a name="wfcexe-workflow-command-line-compiler-tool"></a>wfc.exe (工作流程命令列編譯器工具) 
> [!NOTE]
> 此資料討論已被汰換的類型及命名空間。

wfc.exe 工作流程命令列編譯器工具適用于副檔名為 *xoml* () 的舊工作流程標記檔案。

## <a name="compilation-process"></a>編譯流程

編譯工作流程時，編譯處理程序會執行下列程序：

- 執行驗證，以根據工作流程活動為自己設定的規則確認這些活動是有效的。 如果驗證錯誤，則編譯器會傳回錯誤清單。  
- 從輸入編譯器的標記定義產生部分類別。  

- 產生程式碼來協助活動的執行階段執行。 產生事件訂閱來協助活動知道它們所包含的活動何時完成執行。  
- 從標記檔產生的部分類別和從程式碼檔產生的部分類別會進入 .NET Framework C# 或 Visual Basic 編譯器。 這個程序的輸出為 .NET 組件 WorkflowSample.dll。 您可以部署這個組件來執行工作流程。

### <a name="compiler-options"></a>編譯器選項

本節顯示 wfc.exe 工作流程命令列編譯器的選項。

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

## <a name="remarks"></a>備註
> [!NOTE]
> 此資料討論已被汰換的類型及命名空間。

授權型別的清單通常會在 *wfc.exe.config* 檔案中定義。 在工作流程編譯的驗證階段期間，如果工作流程來源文件或隨附規則檔案直接參考任何未出現在授權類型清單中的 .NET Framework 類型，則會拒絕該工作流程來源文件。 授權型別的清單是 XML 檔，其中每個專案都指出 `Assembly` 、、 `Namespace` `TypeName` 和授權的 { `True`&#124;`False` } 指標。 `AuthorizedType` 對應至清單中的專案。 允許用來包含或排除完整命名空間的萬用字元標記法。 例如， `Type="System.*"` 包含中的所有類型 <xref:System> ，包括子命名空間中包含的類型。
  
授權類型清單的使用是由選項所控制 <xref:System.Workflow.ComponentModel.Compiler.WorkflowCompiler> `'/checktypes'` 。

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
> 當 `Type="System.*"` 類型存在時，可以包含其他非預期的類型（例如 `Type="System.Configuration"` ）進行編譯。 您應該小心並檢查每一個。 對於任何應該限制的類型，請務必將設定 `Authorized` 為 `False` 。

## <a name="see-also"></a>請參閱

- [AuthorizedType 類別](xref:System.Workflow.ComponentModel.Compiler.AuthorizedType)
