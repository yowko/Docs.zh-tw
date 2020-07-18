---
title: 設定區段架構
ms.date: 05/02/2017
helpviewer_keywords:
- configuration settings [.NET Framework], custom
- schema configuration settings
- configuration sections [.NET Framework]
- custom elements
- configuration schema [.NET Framework], custom settings in configuration files
- elements [.NET Framework], custom settings in configuration files
ms.assetid: 6e4cc793-c526-4007-b4e9-37d56295f2cb
ms.openlocfilehash: fc43a9c32ba33629b6e89120cf57f6d212ab3a56
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441657"
---
# <a name="configuration-sections-schema"></a>設定區段架構

設定區段架構包含的元素會定義設定檔案中的自訂設定。 如需設定檔案和架構的一般資訊，請參閱[.NET Framework 的設定檔架構](index.md)。

[**\<configuration>**](configuration-element.md)
[**\<configSections>**](configsections-element-for-configuration.md)
[**\<section>**](section-element.md)
[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)

|     | 描述 |
| --- | ----------- |
| [**\<configSections>**](configsections-element-for-configuration.md) | 包含設定區段和命名空間宣告。 |
| [**\<section>** 針對 **\<configSections>** 和**\<sectionGroup>**](section-element.md) | 包含設定區段宣告。 |
| [**\<sectionGroup>** 對於**\<configSections>**](sectiongroup-element-for-configsections.md) | 定義設定區段的命名空間。 |

<a name="dep"></a>

## <a name="unimplemented-elements"></a>未實現的元素

下列元素不會有任何影響，因此不應使用：

* **\<clear>**
* **\<remove>**
