---
title: Windows Form 組態區段
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
ms.openlocfilehash: 4de61ae3cb5eb8a3fc226881e2b7f842030dfddf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151828"
---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="6ac71-102">Windows Form 組態區段</span><span class="sxs-lookup"><span data-stu-id="6ac71-102">Windows Forms Configuration Section</span></span>
<span data-ttu-id="6ac71-103">Windows Forms 組態設定允許 Windows Forms 應用程式儲存並擷取有關自訂應用程式設定 (例如多重監視器支援、高 DPI 支援，以及其他預先定義的組態設定) 的資訊。</span><span class="sxs-lookup"><span data-stu-id="6ac71-103">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="6ac71-104">Windows Forms 應用程式組態設定是儲存在應用程式組態檔的 `System.Windows.Forms.ApplicationConfigurationSection` 元素中。</span><span class="sxs-lookup"><span data-stu-id="6ac71-104">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ApplicationConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="6ac71-105">語法</span><span class="sxs-lookup"><span data-stu-id="6ac71-105">Syntax</span></span>

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6ac71-106">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="6ac71-106">Attributes and elements</span></span>

<span data-ttu-id="6ac71-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6ac71-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6ac71-108">屬性</span><span class="sxs-lookup"><span data-stu-id="6ac71-108">Attributes</span></span>

<span data-ttu-id="6ac71-109">無。</span><span class="sxs-lookup"><span data-stu-id="6ac71-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6ac71-110">子元素</span><span class="sxs-lookup"><span data-stu-id="6ac71-110">Child elements</span></span>

<span data-ttu-id="6ac71-111">元素</span><span class="sxs-lookup"><span data-stu-id="6ac71-111">Element</span></span>  |<span data-ttu-id="6ac71-112">描述</span><span class="sxs-lookup"><span data-stu-id="6ac71-112">Description</span></span> |
---------|---------|
[`<add>`](windows-forms-add-configuration-element.md) | <span data-ttu-id="6ac71-113">新增具有指定值的組態設定金鑰</span><span class="sxs-lookup"><span data-stu-id="6ac71-113">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="6ac71-114">父元素</span><span class="sxs-lookup"><span data-stu-id="6ac71-114">Parent elements</span></span>

<span data-ttu-id="6ac71-115">元素</span><span class="sxs-lookup"><span data-stu-id="6ac71-115">Element</span></span>  |<span data-ttu-id="6ac71-116">描述</span><span class="sxs-lookup"><span data-stu-id="6ac71-116">Description</span></span> |
---------|---------|
[<span data-ttu-id="6ac71-117">\<配置></span><span class="sxs-lookup"><span data-stu-id="6ac71-117">\<configuration></span></span>](../configuration-element.md) | <span data-ttu-id="6ac71-118">通用語言執行平台和 Windows Forms 應用程式所使用之每個組態檔中的根元素</span><span class="sxs-lookup"><span data-stu-id="6ac71-118">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="6ac71-119">備註</span><span class="sxs-lookup"><span data-stu-id="6ac71-119">Remarks</span></span>

<span data-ttu-id="6ac71-120">從 .NET Framework 4.7 開始，`<System.Windows.Forms.ApplicationConfigurationSection>` 元素能允許您設定 Windows Forms 應用程式，以利用 .NET Framework 最新版本中的新增功能。</span><span class="sxs-lookup"><span data-stu-id="6ac71-120">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ApplicationConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span>

<span data-ttu-id="6ac71-121">該`<System.Windows.Forms.ApplicationConfigurationSection>`元素可以包括一個或多個子項目[`<add>`](windows-forms-add-configuration-element.md)，每個子項目定義特定的配置設置。</span><span class="sxs-lookup"><span data-stu-id="6ac71-121">The `<System.Windows.Forms.ApplicationConfigurationSection>` element can include one or more child [`<add>`](windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ac71-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ac71-122">See also</span></span>

- [<span data-ttu-id="6ac71-123">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="6ac71-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6ac71-124">Windows 表單中的高 DPI 支援</span><span class="sxs-lookup"><span data-stu-id="6ac71-124">High DPI Support in Windows Forms</span></span>](../../../winforms/high-dpi-support-in-windows-forms.md)
