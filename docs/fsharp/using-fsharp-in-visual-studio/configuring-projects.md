---
title: '設定專案 （F #）'
description: '了解如何使用 專案設計工具，當您使用 Visual Studio 中的 F # 專案。'
ms.date: 05/16/2016
ms.openlocfilehash: a6c9539945bbd32748ffca1434c984402bc3f17b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="configuring-projects-in-visual-studio"></a>Visual Studio 中設定專案

> [!NOTE]
這篇文章不是最新的 Visual Studio 中的最新狀態。  將會更新。

本主題包含有關如何使用資訊**專案設計工具**當您使用 F # 專案。 使用 F # 專案不是明顯不同於使用 Visual Basic 或 C# 專案。 您可以在您使用 F # 時經常使用一般的 Visual Studio 專案文件做為您主要的參考。 本主題提供與其他 Visual Studio 語言共用設定的 Visual Studio 文件中的相關資訊的連結，並也會說明 F # 的特定設定。

## <a name="project-designer"></a>專案設計工具
**專案設計工具**和其一般用法主題所述完全[專案設計工具簡介](https://msdn.microsoft.com/library/898dd854-c98d-430c-ba1b-a913ce3c73d7)Visual Studio 文件中。 **專案設計工具**分組相關功能的數個頁面所組成。 適用於 F # 專案的頁面是主要是供其他語言的子集。 下表將描述支援 F # 中的頁面。 沒有可用的頁面與相關的功能時無法使用在 F # 中，或可用的只是藉由變更命令列選項。 F # 中可用的頁面類似於 C# 頁面的最接近，因此與相關的 C# 提供的連結**專案設計工具**頁面。

|專案設計工具 頁面|相關的連結|描述|
|---------------------|-------------|-----------|
|`Application`|[應用程式 頁面上，專案設計工具&#40;C&#35;&#41;](https://msdn.microsoft.com/library/ms247046.aspx)|可讓您指定應用程式層級設定和屬性，例如您要建立文件庫或可執行檔，應用程式的目標.NET Framework 版本，而且其中資源之檔案的相關資訊的應用程式儲存使用。|
|`Build`|[專案設計工具、 建置頁&#40;C&#35;&#41;](https://msdn.microsoft.com/library/kb4wyys2.aspx)|可讓您控制如何編譯程式碼。|
|`Build Events`|[專案設計工具、 建置事件頁面&#40;C&#35;&#41;](https://msdn.microsoft.com/library/kb4wyys2.aspx)|可讓您指定命令執行之前或之後的編譯。|
|`Debug`|[專案設計工具、偵錯頁面](https://msdn.microsoft.com/library/2wcdezs5.aspx)|可讓您控制如何在偵錯期間執行應用程式。 這包括哪些命令列以使用與您的應用程式的起始目錄為何，以及任何特殊的偵錯的模式，您想要啟用，例如原生程式碼和 SQL。|
|`Reference Paths`|[管理專案中的參考](/visualstudio/ide/managing-references-in-a-project)|可讓您指定要搜尋組件取決於程式碼的位置。|

## <a name="f-specific-settings"></a>F #-特定的設定
下表摘要說明特定 F # 設定：

|專案設計工具 頁面|設定|描述|
|---------------------|-------|-----------|
|`Build`|`Generate tail calls`|如果選取，可讓您使用 Microsoft intermediate language (MSIL) 指令的結尾。 這會造成可重複使用之結尾遞迴函式的堆疊框架。 相當於`--tailcalls`編譯器選項。|
|`Build`|`Other flags`|可讓您指定其他編譯器命令列選項。|

## <a name="see-also"></a>另請參閱
 [開始使用 F # Visual Studio 中](../get-started/get-started-visual-studio.md)  
 [編譯器選項](../language-reference/compiler-options.md)  
 [專案設計工具簡介](https://msdn.microsoft.com/library/898dd854-c98d-430c-ba1b-a913ce3c73d7(v=vs.100))
