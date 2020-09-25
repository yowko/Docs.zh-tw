---
title: OLE DB 結構描述集合
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 90899a123b3dafcd47a50ef8f6eb003938b22a03
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186935"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="cb46d-102">OLE DB 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="cb46d-102">OLE DB Schema Collections</span></span>

<span data-ttu-id="cb46d-103">本節將討論 Microsoft SQL Server、Oracle 和 Microsoft Jet 之 OLE DB 提供者的結構描述集合支援。</span><span class="sxs-lookup"><span data-stu-id="cb46d-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="cb46d-104">Microsoft SQL Server OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="cb46d-104">Microsoft SQL Server OLE DB Provider</span></span>  

 <span data-ttu-id="cb46d-105">除了通用結構描述集合之外，Microsoft SQL Server OLE DB 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="cb46d-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="cb46d-106">資料表</span><span class="sxs-lookup"><span data-stu-id="cb46d-106">Tables</span></span>  
  
- <span data-ttu-id="cb46d-107">資料行</span><span class="sxs-lookup"><span data-stu-id="cb46d-107">Columns</span></span>  
  
- <span data-ttu-id="cb46d-108">程序</span><span class="sxs-lookup"><span data-stu-id="cb46d-108">Procedures</span></span>  
  
- <span data-ttu-id="cb46d-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="cb46d-109">ProcedureParameters</span></span>  
  
- <span data-ttu-id="cb46d-110">目錄</span><span class="sxs-lookup"><span data-stu-id="cb46d-110">Catalog</span></span>  
  
- <span data-ttu-id="cb46d-111">索引</span><span class="sxs-lookup"><span data-stu-id="cb46d-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="cb46d-112">資料表</span><span class="sxs-lookup"><span data-stu-id="cb46d-112">Tables</span></span>  
  
|<span data-ttu-id="cb46d-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cb46d-113">ColumnName</span></span>|<span data-ttu-id="cb46d-114">DataType</span><span class="sxs-lookup"><span data-stu-id="cb46d-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cb46d-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cb46d-115">TABLE_CATALOG</span></span>|<span data-ttu-id="cb46d-116">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-116">String</span></span>|  
|<span data-ttu-id="cb46d-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cb46d-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="cb46d-118">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-118">String</span></span>|  
|<span data-ttu-id="cb46d-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-119">TABLE_NAME</span></span>|<span data-ttu-id="cb46d-120">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-120">String</span></span>|  
|<span data-ttu-id="cb46d-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="cb46d-121">TABLE_TYPE</span></span>|<span data-ttu-id="cb46d-122">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-122">String</span></span>|  
|<span data-ttu-id="cb46d-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="cb46d-123">TABLE_GUID</span></span>|<span data-ttu-id="cb46d-124">Guid</span><span class="sxs-lookup"><span data-stu-id="cb46d-124">Guid</span></span>|  
|<span data-ttu-id="cb46d-125">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cb46d-125">DESCRIPTION</span></span>|<span data-ttu-id="cb46d-126">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-126">String</span></span>|  
|<span data-ttu-id="cb46d-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="cb46d-127">TABLE_PROPID</span></span>|<span data-ttu-id="cb46d-128">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-128">Int64</span></span>|  
|<span data-ttu-id="cb46d-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="cb46d-129">DATE_CREATED</span></span>|<span data-ttu-id="cb46d-130">Datetime</span><span class="sxs-lookup"><span data-stu-id="cb46d-130">DateTime</span></span>|  
|<span data-ttu-id="cb46d-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="cb46d-131">DATE_MODIFIED</span></span>|<span data-ttu-id="cb46d-132">Datetime</span><span class="sxs-lookup"><span data-stu-id="cb46d-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="cb46d-133">資料行</span><span class="sxs-lookup"><span data-stu-id="cb46d-133">Columns</span></span>  
  
|<span data-ttu-id="cb46d-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cb46d-134">ColumnName</span></span>|<span data-ttu-id="cb46d-135">DataType</span><span class="sxs-lookup"><span data-stu-id="cb46d-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cb46d-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cb46d-136">TABLE_CATALOG</span></span>|<span data-ttu-id="cb46d-137">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-137">String</span></span>|  
|<span data-ttu-id="cb46d-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cb46d-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="cb46d-139">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-139">String</span></span>|  
|<span data-ttu-id="cb46d-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-140">TABLE_NAME</span></span>|<span data-ttu-id="cb46d-141">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-141">String</span></span>|  
|<span data-ttu-id="cb46d-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-142">COLUMN_NAME</span></span>|<span data-ttu-id="cb46d-143">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-143">String</span></span>|  
|<span data-ttu-id="cb46d-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="cb46d-144">COLUMN_GUID</span></span>|<span data-ttu-id="cb46d-145">Guid</span><span class="sxs-lookup"><span data-stu-id="cb46d-145">Guid</span></span>|  
|<span data-ttu-id="cb46d-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="cb46d-146">COLUMN_PROPID</span></span>|<span data-ttu-id="cb46d-147">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-147">Int64</span></span>|  
|<span data-ttu-id="cb46d-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cb46d-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="cb46d-149">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-149">Int64</span></span>|  
|<span data-ttu-id="cb46d-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="cb46d-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="cb46d-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-151">Boolean</span></span>|  
|<span data-ttu-id="cb46d-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="cb46d-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="cb46d-153">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-153">String</span></span>|  
|<span data-ttu-id="cb46d-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="cb46d-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="cb46d-155">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-155">Int64</span></span>|  
|<span data-ttu-id="cb46d-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="cb46d-156">IS_NULLABLE</span></span>|<span data-ttu-id="cb46d-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-157">Boolean</span></span>|  
|<span data-ttu-id="cb46d-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cb46d-158">DATA_TYPE</span></span>|<span data-ttu-id="cb46d-159">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-159">Int32</span></span>|  
|<span data-ttu-id="cb46d-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="cb46d-160">TYPE_GUID</span></span>|<span data-ttu-id="cb46d-161">Guid</span><span class="sxs-lookup"><span data-stu-id="cb46d-161">Guid</span></span>|  
|<span data-ttu-id="cb46d-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cb46d-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="cb46d-163">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-163">Int64</span></span>|  
|<span data-ttu-id="cb46d-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cb46d-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="cb46d-165">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-165">Int64</span></span>|  
|<span data-ttu-id="cb46d-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="cb46d-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="cb46d-167">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-167">Int32</span></span>|  
|<span data-ttu-id="cb46d-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="cb46d-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="cb46d-169">Int16</span><span class="sxs-lookup"><span data-stu-id="cb46d-169">Int16</span></span>|  
|<span data-ttu-id="cb46d-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="cb46d-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="cb46d-171">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-171">Int64</span></span>|  
|<span data-ttu-id="cb46d-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cb46d-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="cb46d-173">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-173">String</span></span>|  
|<span data-ttu-id="cb46d-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cb46d-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="cb46d-175">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-175">String</span></span>|  
|<span data-ttu-id="cb46d-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="cb46d-177">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-177">String</span></span>|  
|<span data-ttu-id="cb46d-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cb46d-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="cb46d-179">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-179">String</span></span>|  
|<span data-ttu-id="cb46d-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cb46d-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="cb46d-181">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-181">String</span></span>|  
|<span data-ttu-id="cb46d-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-182">COLLATION_NAME</span></span>|<span data-ttu-id="cb46d-183">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-183">String</span></span>|  
|<span data-ttu-id="cb46d-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cb46d-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="cb46d-185">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-185">String</span></span>|  
|<span data-ttu-id="cb46d-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cb46d-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="cb46d-187">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-187">String</span></span>|  
|<span data-ttu-id="cb46d-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-188">DOMAIN_NAME</span></span>|<span data-ttu-id="cb46d-189">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-189">String</span></span>|  
|<span data-ttu-id="cb46d-190">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cb46d-190">DESCRIPTION</span></span>|<span data-ttu-id="cb46d-191">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-191">String</span></span>|  
|<span data-ttu-id="cb46d-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="cb46d-192">COLUMN_LCID</span></span>|<span data-ttu-id="cb46d-193">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-193">Int32</span></span>|  
|<span data-ttu-id="cb46d-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="cb46d-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="cb46d-195">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-195">Int32</span></span>|  
|<span data-ttu-id="cb46d-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="cb46d-196">COLUMN_SORTID</span></span>|<span data-ttu-id="cb46d-197">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-197">Int32</span></span>|  
|<span data-ttu-id="cb46d-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="cb46d-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="cb46d-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="cb46d-199">Byte[]</span></span>|  
|<span data-ttu-id="cb46d-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="cb46d-200">IS_COMPUTED</span></span>|<span data-ttu-id="cb46d-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="cb46d-202">程序</span><span class="sxs-lookup"><span data-stu-id="cb46d-202">Procedures</span></span>  
  
|<span data-ttu-id="cb46d-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cb46d-203">ColumnName</span></span>|<span data-ttu-id="cb46d-204">DataType</span><span class="sxs-lookup"><span data-stu-id="cb46d-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cb46d-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cb46d-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="cb46d-206">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-206">String</span></span>|  
|<span data-ttu-id="cb46d-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cb46d-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="cb46d-208">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-208">String</span></span>|  
|<span data-ttu-id="cb46d-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="cb46d-210">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-210">String</span></span>|  
|<span data-ttu-id="cb46d-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="cb46d-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="cb46d-212">Int16</span><span class="sxs-lookup"><span data-stu-id="cb46d-212">Int16</span></span>|  
|<span data-ttu-id="cb46d-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="cb46d-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="cb46d-214">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-214">String</span></span>|  
|<span data-ttu-id="cb46d-215">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cb46d-215">DESCRIPTION</span></span>|<span data-ttu-id="cb46d-216">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-216">String</span></span>|  
|<span data-ttu-id="cb46d-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="cb46d-217">DATE_CREATED</span></span>|<span data-ttu-id="cb46d-218">Datetime</span><span class="sxs-lookup"><span data-stu-id="cb46d-218">DateTime</span></span>|  
|<span data-ttu-id="cb46d-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="cb46d-219">DATE_MODIFIED</span></span>|<span data-ttu-id="cb46d-220">Datetime</span><span class="sxs-lookup"><span data-stu-id="cb46d-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="cb46d-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="cb46d-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="cb46d-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cb46d-222">ColumnName</span></span>|<span data-ttu-id="cb46d-223">DataType</span><span class="sxs-lookup"><span data-stu-id="cb46d-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cb46d-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cb46d-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="cb46d-225">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-225">String</span></span>|  
|<span data-ttu-id="cb46d-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cb46d-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="cb46d-227">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-227">String</span></span>|  
|<span data-ttu-id="cb46d-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="cb46d-229">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-229">String</span></span>|  
|<span data-ttu-id="cb46d-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-230">PARAMETER_NAME</span></span>|<span data-ttu-id="cb46d-231">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-231">String</span></span>|  
|<span data-ttu-id="cb46d-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cb46d-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="cb46d-233">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-233">Int32</span></span>|  
|<span data-ttu-id="cb46d-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="cb46d-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="cb46d-235">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-235">Int32</span></span>|  
|<span data-ttu-id="cb46d-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="cb46d-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="cb46d-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-237">Boolean</span></span>|  
|<span data-ttu-id="cb46d-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="cb46d-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="cb46d-239">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-239">String</span></span>|  
|<span data-ttu-id="cb46d-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="cb46d-240">IS_NULLABLE</span></span>|<span data-ttu-id="cb46d-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-241">Boolean</span></span>|  
|<span data-ttu-id="cb46d-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cb46d-242">DATA_TYPE</span></span>|<span data-ttu-id="cb46d-243">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-243">Int32</span></span>|  
|<span data-ttu-id="cb46d-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cb46d-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="cb46d-245">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-245">Int64</span></span>|  
|<span data-ttu-id="cb46d-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cb46d-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="cb46d-247">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-247">Int64</span></span>|  
|<span data-ttu-id="cb46d-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="cb46d-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="cb46d-249">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-249">Int32</span></span>|  
|<span data-ttu-id="cb46d-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="cb46d-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="cb46d-251">Int16</span><span class="sxs-lookup"><span data-stu-id="cb46d-251">Int16</span></span>|  
|<span data-ttu-id="cb46d-252">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cb46d-252">DESCRIPTION</span></span>|<span data-ttu-id="cb46d-253">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-253">String</span></span>|  
|<span data-ttu-id="cb46d-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-254">TYPE_NAME</span></span>|<span data-ttu-id="cb46d-255">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-255">String</span></span>|  
|<span data-ttu-id="cb46d-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="cb46d-257">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="cb46d-258">目錄</span><span class="sxs-lookup"><span data-stu-id="cb46d-258">Catalog</span></span>  
  
|<span data-ttu-id="cb46d-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cb46d-259">ColumnName</span></span>|<span data-ttu-id="cb46d-260">DataType</span><span class="sxs-lookup"><span data-stu-id="cb46d-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cb46d-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-261">CATALOG_NAME</span></span>|<span data-ttu-id="cb46d-262">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-262">String</span></span>|  
|<span data-ttu-id="cb46d-263">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cb46d-263">DESCRIPTION</span></span>|<span data-ttu-id="cb46d-264">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="cb46d-265">索引</span><span class="sxs-lookup"><span data-stu-id="cb46d-265">Indexes</span></span>  
  
|<span data-ttu-id="cb46d-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cb46d-266">ColumnName</span></span>|<span data-ttu-id="cb46d-267">DataType</span><span class="sxs-lookup"><span data-stu-id="cb46d-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cb46d-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cb46d-268">TABLE_CATALOG</span></span>|<span data-ttu-id="cb46d-269">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-269">String</span></span>|  
|<span data-ttu-id="cb46d-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cb46d-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="cb46d-271">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-271">String</span></span>|  
|<span data-ttu-id="cb46d-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-272">TABLE_NAME</span></span>|<span data-ttu-id="cb46d-273">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-273">String</span></span>|  
|<span data-ttu-id="cb46d-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cb46d-274">INDEX_CATALOG</span></span>|<span data-ttu-id="cb46d-275">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-275">String</span></span>|  
|<span data-ttu-id="cb46d-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cb46d-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="cb46d-277">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-277">String</span></span>|  
|<span data-ttu-id="cb46d-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-278">INDEX_NAME</span></span>|<span data-ttu-id="cb46d-279">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-279">String</span></span>|  
|<span data-ttu-id="cb46d-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="cb46d-280">PRIMARY_KEY</span></span>|<span data-ttu-id="cb46d-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-281">Boolean</span></span>|  
|<span data-ttu-id="cb46d-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="cb46d-282">UNIQUE</span></span>|<span data-ttu-id="cb46d-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-283">Boolean</span></span>|  
|<span data-ttu-id="cb46d-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="cb46d-284">CLUSTERED</span></span>|<span data-ttu-id="cb46d-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-285">Boolean</span></span>|  
|<span data-ttu-id="cb46d-286">TYPE</span><span class="sxs-lookup"><span data-stu-id="cb46d-286">TYPE</span></span>|<span data-ttu-id="cb46d-287">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-287">Int32</span></span>|  
|<span data-ttu-id="cb46d-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="cb46d-288">FILL_FACTOR</span></span>|<span data-ttu-id="cb46d-289">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-289">Int32</span></span>|  
|<span data-ttu-id="cb46d-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="cb46d-290">INITIAL_SIZE</span></span>|<span data-ttu-id="cb46d-291">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-291">Int32</span></span>|  
|<span data-ttu-id="cb46d-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="cb46d-292">NULLS</span></span>|<span data-ttu-id="cb46d-293">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-293">Int32</span></span>|  
|<span data-ttu-id="cb46d-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="cb46d-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="cb46d-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-295">Boolean</span></span>|  
|<span data-ttu-id="cb46d-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="cb46d-296">AUTO_UPDATE</span></span>|<span data-ttu-id="cb46d-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-297">Boolean</span></span>|  
|<span data-ttu-id="cb46d-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="cb46d-298">NULL_COLLATION</span></span>|<span data-ttu-id="cb46d-299">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-299">Int32</span></span>|  
|<span data-ttu-id="cb46d-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cb46d-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="cb46d-301">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-301">Int64</span></span>|  
|<span data-ttu-id="cb46d-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-302">COLUMN_NAME</span></span>|<span data-ttu-id="cb46d-303">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-303">String</span></span>|  
|<span data-ttu-id="cb46d-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="cb46d-304">COLUMN_GUID</span></span>|<span data-ttu-id="cb46d-305">Guid</span><span class="sxs-lookup"><span data-stu-id="cb46d-305">Guid</span></span>|  
|<span data-ttu-id="cb46d-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="cb46d-306">COLUMN_PROPID</span></span>|<span data-ttu-id="cb46d-307">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-307">Int64</span></span>|  
|<span data-ttu-id="cb46d-308">COLLATION</span><span class="sxs-lookup"><span data-stu-id="cb46d-308">COLLATION</span></span>|<span data-ttu-id="cb46d-309">Int16</span><span class="sxs-lookup"><span data-stu-id="cb46d-309">Int16</span></span>|  
|<span data-ttu-id="cb46d-310">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="cb46d-310">CARDINALITY</span></span>|<span data-ttu-id="cb46d-311">Decimal</span><span class="sxs-lookup"><span data-stu-id="cb46d-311">Decimal</span></span>|  
|<span data-ttu-id="cb46d-312">PAGES</span><span class="sxs-lookup"><span data-stu-id="cb46d-312">PAGES</span></span>|<span data-ttu-id="cb46d-313">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-313">Int32</span></span>|  
|<span data-ttu-id="cb46d-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="cb46d-314">FILTER_CONDITION</span></span>|<span data-ttu-id="cb46d-315">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-315">String</span></span>|  
|<span data-ttu-id="cb46d-316">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="cb46d-316">INTEGRATED</span></span>|<span data-ttu-id="cb46d-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="cb46d-318">Microsoft Oracle OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="cb46d-318">Microsoft Oracle OLE DB Provider</span></span>  

 <span data-ttu-id="cb46d-319">除了通用結構描述集合之外，Microsoft Oracle OLE DB 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="cb46d-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="cb46d-320">資料表</span><span class="sxs-lookup"><span data-stu-id="cb46d-320">Tables</span></span>  
  
- <span data-ttu-id="cb46d-321">資料行</span><span class="sxs-lookup"><span data-stu-id="cb46d-321">Columns</span></span>  
  
- <span data-ttu-id="cb46d-322">程序</span><span class="sxs-lookup"><span data-stu-id="cb46d-322">Procedures</span></span>  
  
- <span data-ttu-id="cb46d-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="cb46d-323">ProcedureColumns</span></span>  
  
- <span data-ttu-id="cb46d-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="cb46d-324">ProcedureParameters</span></span>  
  
- <span data-ttu-id="cb46d-325">檢視</span><span class="sxs-lookup"><span data-stu-id="cb46d-325">Views</span></span>  
  
- <span data-ttu-id="cb46d-326">索引</span><span class="sxs-lookup"><span data-stu-id="cb46d-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="cb46d-327">資料表</span><span class="sxs-lookup"><span data-stu-id="cb46d-327">Tables</span></span>  
  
|<span data-ttu-id="cb46d-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cb46d-328">ColumnName</span></span>|<span data-ttu-id="cb46d-329">DataType</span><span class="sxs-lookup"><span data-stu-id="cb46d-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cb46d-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cb46d-330">TABLE_CATALOG</span></span>|<span data-ttu-id="cb46d-331">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-331">String</span></span>|  
|<span data-ttu-id="cb46d-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cb46d-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="cb46d-333">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-333">String</span></span>|  
|<span data-ttu-id="cb46d-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-334">TABLE_NAME</span></span>|<span data-ttu-id="cb46d-335">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-335">String</span></span>|  
|<span data-ttu-id="cb46d-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="cb46d-336">TABLE_TYPE</span></span>|<span data-ttu-id="cb46d-337">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-337">String</span></span>|  
|<span data-ttu-id="cb46d-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="cb46d-338">TABLE_GUID</span></span>|<span data-ttu-id="cb46d-339">Guid</span><span class="sxs-lookup"><span data-stu-id="cb46d-339">Guid</span></span>|  
|<span data-ttu-id="cb46d-340">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cb46d-340">DESCRIPTION</span></span>|<span data-ttu-id="cb46d-341">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-341">String</span></span>|  
|<span data-ttu-id="cb46d-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="cb46d-342">TABLE_PROPID</span></span>|<span data-ttu-id="cb46d-343">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-343">Int64</span></span>|  
|<span data-ttu-id="cb46d-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="cb46d-344">DATE_CREATED</span></span>|<span data-ttu-id="cb46d-345">Datetime</span><span class="sxs-lookup"><span data-stu-id="cb46d-345">DateTime</span></span>|  
|<span data-ttu-id="cb46d-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="cb46d-346">DATE_MODIFIED</span></span>|<span data-ttu-id="cb46d-347">Datetime</span><span class="sxs-lookup"><span data-stu-id="cb46d-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="cb46d-348">資料行</span><span class="sxs-lookup"><span data-stu-id="cb46d-348">Columns</span></span>  
  
|<span data-ttu-id="cb46d-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cb46d-349">ColumnName</span></span>|<span data-ttu-id="cb46d-350">DataType</span><span class="sxs-lookup"><span data-stu-id="cb46d-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cb46d-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cb46d-351">TABLE_CATALOG</span></span>|<span data-ttu-id="cb46d-352">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-352">String</span></span>|  
|<span data-ttu-id="cb46d-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cb46d-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="cb46d-354">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-354">String</span></span>|  
|<span data-ttu-id="cb46d-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-355">TABLE_NAME</span></span>|<span data-ttu-id="cb46d-356">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-356">String</span></span>|  
|<span data-ttu-id="cb46d-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-357">COLUMN_NAME</span></span>|<span data-ttu-id="cb46d-358">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-358">String</span></span>|  
|<span data-ttu-id="cb46d-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="cb46d-359">COLUMN_GUID</span></span>|<span data-ttu-id="cb46d-360">Guid</span><span class="sxs-lookup"><span data-stu-id="cb46d-360">Guid</span></span>|  
|<span data-ttu-id="cb46d-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="cb46d-361">COLUMN_PROPID</span></span>|<span data-ttu-id="cb46d-362">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-362">Int64</span></span>|  
|<span data-ttu-id="cb46d-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cb46d-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="cb46d-364">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-364">Int64</span></span>|  
|<span data-ttu-id="cb46d-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="cb46d-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="cb46d-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-366">Boolean</span></span>|  
|<span data-ttu-id="cb46d-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="cb46d-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="cb46d-368">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-368">String</span></span>|  
|<span data-ttu-id="cb46d-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="cb46d-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="cb46d-370">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-370">Int64</span></span>|  
|<span data-ttu-id="cb46d-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="cb46d-371">IS_NULLABLE</span></span>|<span data-ttu-id="cb46d-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-372">Boolean</span></span>|  
|<span data-ttu-id="cb46d-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cb46d-373">DATA_TYPE</span></span>|<span data-ttu-id="cb46d-374">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-374">Int32</span></span>|  
|<span data-ttu-id="cb46d-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="cb46d-375">TYPE_GUID</span></span>|<span data-ttu-id="cb46d-376">Guid</span><span class="sxs-lookup"><span data-stu-id="cb46d-376">Guid</span></span>|  
|<span data-ttu-id="cb46d-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cb46d-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="cb46d-378">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-378">Int64</span></span>|  
|<span data-ttu-id="cb46d-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cb46d-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="cb46d-380">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-380">Int64</span></span>|  
|<span data-ttu-id="cb46d-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="cb46d-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="cb46d-382">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-382">Int32</span></span>|  
|<span data-ttu-id="cb46d-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="cb46d-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="cb46d-384">Int16</span><span class="sxs-lookup"><span data-stu-id="cb46d-384">Int16</span></span>|  
|<span data-ttu-id="cb46d-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="cb46d-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="cb46d-386">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-386">Int64</span></span>|  
|<span data-ttu-id="cb46d-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cb46d-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="cb46d-388">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-388">String</span></span>|  
|<span data-ttu-id="cb46d-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cb46d-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="cb46d-390">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-390">String</span></span>|  
|<span data-ttu-id="cb46d-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="cb46d-392">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-392">String</span></span>|  
|<span data-ttu-id="cb46d-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cb46d-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="cb46d-394">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-394">String</span></span>|  
|<span data-ttu-id="cb46d-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cb46d-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="cb46d-396">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-396">String</span></span>|  
|<span data-ttu-id="cb46d-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-397">COLLATION_NAME</span></span>|<span data-ttu-id="cb46d-398">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-398">String</span></span>|  
|<span data-ttu-id="cb46d-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cb46d-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="cb46d-400">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-400">String</span></span>|  
|<span data-ttu-id="cb46d-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cb46d-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="cb46d-402">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-402">String</span></span>|  
|<span data-ttu-id="cb46d-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-403">DOMAIN_NAME</span></span>|<span data-ttu-id="cb46d-404">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-404">String</span></span>|  
|<span data-ttu-id="cb46d-405">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cb46d-405">DESCRIPTION</span></span>|<span data-ttu-id="cb46d-406">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="cb46d-407">程序</span><span class="sxs-lookup"><span data-stu-id="cb46d-407">Procedures</span></span>  
  
|<span data-ttu-id="cb46d-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cb46d-408">ColumnName</span></span>|<span data-ttu-id="cb46d-409">DataType</span><span class="sxs-lookup"><span data-stu-id="cb46d-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cb46d-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cb46d-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="cb46d-411">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-411">String</span></span>|  
|<span data-ttu-id="cb46d-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cb46d-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="cb46d-413">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-413">String</span></span>|  
|<span data-ttu-id="cb46d-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="cb46d-415">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-415">String</span></span>|  
|<span data-ttu-id="cb46d-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="cb46d-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="cb46d-417">Int16</span><span class="sxs-lookup"><span data-stu-id="cb46d-417">Int16</span></span>|  
|<span data-ttu-id="cb46d-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="cb46d-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="cb46d-419">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-419">String</span></span>|  
|<span data-ttu-id="cb46d-420">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cb46d-420">DESCRIPTION</span></span>|<span data-ttu-id="cb46d-421">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-421">String</span></span>|  
|<span data-ttu-id="cb46d-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="cb46d-422">DATE_CREATED</span></span>|<span data-ttu-id="cb46d-423">Datetime</span><span class="sxs-lookup"><span data-stu-id="cb46d-423">DateTime</span></span>|  
|<span data-ttu-id="cb46d-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="cb46d-424">DATE_MODIFIED</span></span>|<span data-ttu-id="cb46d-425">Datetime</span><span class="sxs-lookup"><span data-stu-id="cb46d-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="cb46d-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="cb46d-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="cb46d-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cb46d-427">ColumnName</span></span>|<span data-ttu-id="cb46d-428">DataType</span><span class="sxs-lookup"><span data-stu-id="cb46d-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cb46d-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cb46d-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="cb46d-430">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-430">String</span></span>|  
|<span data-ttu-id="cb46d-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cb46d-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="cb46d-432">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-432">String</span></span>|  
|<span data-ttu-id="cb46d-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="cb46d-434">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-434">String</span></span>|  
|<span data-ttu-id="cb46d-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-435">COLUMN_NAME</span></span>|<span data-ttu-id="cb46d-436">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-436">String</span></span>|  
|<span data-ttu-id="cb46d-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="cb46d-437">COLUMN_GUID</span></span>|<span data-ttu-id="cb46d-438">Guid</span><span class="sxs-lookup"><span data-stu-id="cb46d-438">Guid</span></span>|  
|<span data-ttu-id="cb46d-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="cb46d-439">COLUMN_PROPID</span></span>|<span data-ttu-id="cb46d-440">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-440">Int64</span></span>|  
|<span data-ttu-id="cb46d-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="cb46d-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="cb46d-442">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-442">Int64</span></span>|  
|<span data-ttu-id="cb46d-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cb46d-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="cb46d-444">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-444">Int64</span></span>|  
|<span data-ttu-id="cb46d-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="cb46d-445">IS_NULLABLE</span></span>|<span data-ttu-id="cb46d-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-446">Boolean</span></span>|  
|<span data-ttu-id="cb46d-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cb46d-447">DATA_TYPE</span></span>|<span data-ttu-id="cb46d-448">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-448">Int32</span></span>|  
|<span data-ttu-id="cb46d-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="cb46d-449">TYPE_GUID</span></span>|<span data-ttu-id="cb46d-450">Guid</span><span class="sxs-lookup"><span data-stu-id="cb46d-450">Guid</span></span>|  
|<span data-ttu-id="cb46d-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cb46d-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="cb46d-452">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-452">Int64</span></span>|  
|<span data-ttu-id="cb46d-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cb46d-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="cb46d-454">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-454">Int64</span></span>|  
|<span data-ttu-id="cb46d-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="cb46d-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="cb46d-456">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-456">Int32</span></span>|  
|<span data-ttu-id="cb46d-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="cb46d-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="cb46d-458">Int16</span><span class="sxs-lookup"><span data-stu-id="cb46d-458">Int16</span></span>|  
|<span data-ttu-id="cb46d-459">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cb46d-459">DESCRIPTION</span></span>|<span data-ttu-id="cb46d-460">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-460">String</span></span>|  
|<span data-ttu-id="cb46d-461">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="cb46d-461">OVERLOAD</span></span>|<span data-ttu-id="cb46d-462">Int16</span><span class="sxs-lookup"><span data-stu-id="cb46d-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="cb46d-463">檢視</span><span class="sxs-lookup"><span data-stu-id="cb46d-463">Views</span></span>  
  
|<span data-ttu-id="cb46d-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cb46d-464">ColumnName</span></span>|<span data-ttu-id="cb46d-465">DataType</span><span class="sxs-lookup"><span data-stu-id="cb46d-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cb46d-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cb46d-466">TABLE_CATALOG</span></span>|<span data-ttu-id="cb46d-467">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-467">String</span></span>|  
|<span data-ttu-id="cb46d-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cb46d-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="cb46d-469">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-469">String</span></span>|  
|<span data-ttu-id="cb46d-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-470">TABLE_NAME</span></span>|<span data-ttu-id="cb46d-471">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-471">String</span></span>|  
|<span data-ttu-id="cb46d-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="cb46d-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="cb46d-473">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-473">String</span></span>|  
|<span data-ttu-id="cb46d-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="cb46d-474">CHECK_OPTION</span></span>|<span data-ttu-id="cb46d-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-475">Boolean</span></span>|  
|<span data-ttu-id="cb46d-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="cb46d-476">IS_UPDATABLE</span></span>|<span data-ttu-id="cb46d-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-477">Boolean</span></span>|  
|<span data-ttu-id="cb46d-478">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cb46d-478">DESCRIPTION</span></span>|<span data-ttu-id="cb46d-479">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-479">String</span></span>|  
|<span data-ttu-id="cb46d-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="cb46d-480">DATE_CREATED</span></span>|<span data-ttu-id="cb46d-481">Datetime</span><span class="sxs-lookup"><span data-stu-id="cb46d-481">DateTime</span></span>|  
|<span data-ttu-id="cb46d-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="cb46d-482">DATE_MODIFIED</span></span>|<span data-ttu-id="cb46d-483">Datetime</span><span class="sxs-lookup"><span data-stu-id="cb46d-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="cb46d-484">索引</span><span class="sxs-lookup"><span data-stu-id="cb46d-484">Indexes</span></span>  
  
|<span data-ttu-id="cb46d-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cb46d-485">ColumnName</span></span>|<span data-ttu-id="cb46d-486">DataType</span><span class="sxs-lookup"><span data-stu-id="cb46d-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cb46d-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cb46d-487">TABLE_CATALOG</span></span>|<span data-ttu-id="cb46d-488">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-488">String</span></span>|  
|<span data-ttu-id="cb46d-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cb46d-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="cb46d-490">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-490">String</span></span>|  
|<span data-ttu-id="cb46d-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-491">TABLE_NAME</span></span>|<span data-ttu-id="cb46d-492">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-492">String</span></span>|  
|<span data-ttu-id="cb46d-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cb46d-493">INDEX_CATALOG</span></span>|<span data-ttu-id="cb46d-494">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-494">String</span></span>|  
|<span data-ttu-id="cb46d-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cb46d-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="cb46d-496">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-496">String</span></span>|  
|<span data-ttu-id="cb46d-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-497">INDEX_NAME</span></span>|<span data-ttu-id="cb46d-498">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-498">String</span></span>|  
|<span data-ttu-id="cb46d-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="cb46d-499">PRIMARY_KEY</span></span>|<span data-ttu-id="cb46d-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-500">Boolean</span></span>|  
|<span data-ttu-id="cb46d-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="cb46d-501">UNIQUE</span></span>|<span data-ttu-id="cb46d-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-502">Boolean</span></span>|  
|<span data-ttu-id="cb46d-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="cb46d-503">CLUSTERED</span></span>|<span data-ttu-id="cb46d-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-504">Boolean</span></span>|  
|<span data-ttu-id="cb46d-505">TYPE</span><span class="sxs-lookup"><span data-stu-id="cb46d-505">TYPE</span></span>|<span data-ttu-id="cb46d-506">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-506">Int32</span></span>|  
|<span data-ttu-id="cb46d-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="cb46d-507">FILL_FACTOR</span></span>|<span data-ttu-id="cb46d-508">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-508">Int32</span></span>|  
|<span data-ttu-id="cb46d-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="cb46d-509">INITIAL_SIZE</span></span>|<span data-ttu-id="cb46d-510">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-510">Int32</span></span>|  
|<span data-ttu-id="cb46d-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="cb46d-511">NULLS</span></span>|<span data-ttu-id="cb46d-512">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-512">Int32</span></span>|  
|<span data-ttu-id="cb46d-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="cb46d-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="cb46d-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-514">Boolean</span></span>|  
|<span data-ttu-id="cb46d-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="cb46d-515">AUTO_UPDATE</span></span>|<span data-ttu-id="cb46d-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-516">Boolean</span></span>|  
|<span data-ttu-id="cb46d-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="cb46d-517">NULL_COLLATION</span></span>|<span data-ttu-id="cb46d-518">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-518">Int32</span></span>|  
|<span data-ttu-id="cb46d-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cb46d-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="cb46d-520">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-520">Int64</span></span>|  
|<span data-ttu-id="cb46d-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-521">COLUMN_NAME</span></span>|<span data-ttu-id="cb46d-522">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-522">String</span></span>|  
|<span data-ttu-id="cb46d-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="cb46d-523">COLUMN_GUID</span></span>|<span data-ttu-id="cb46d-524">Guid</span><span class="sxs-lookup"><span data-stu-id="cb46d-524">Guid</span></span>|  
|<span data-ttu-id="cb46d-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="cb46d-525">COLUMN_PROPID</span></span>|<span data-ttu-id="cb46d-526">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-526">Int64</span></span>|  
|<span data-ttu-id="cb46d-527">COLLATION</span><span class="sxs-lookup"><span data-stu-id="cb46d-527">COLLATION</span></span>|<span data-ttu-id="cb46d-528">Int16</span><span class="sxs-lookup"><span data-stu-id="cb46d-528">Int16</span></span>|  
|<span data-ttu-id="cb46d-529">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="cb46d-529">CARDINALITY</span></span>|<span data-ttu-id="cb46d-530">Decimal</span><span class="sxs-lookup"><span data-stu-id="cb46d-530">Decimal</span></span>|  
|<span data-ttu-id="cb46d-531">PAGES</span><span class="sxs-lookup"><span data-stu-id="cb46d-531">PAGES</span></span>|<span data-ttu-id="cb46d-532">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-532">Int32</span></span>|  
|<span data-ttu-id="cb46d-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="cb46d-533">FILTER_CONDITION</span></span>|<span data-ttu-id="cb46d-534">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-534">String</span></span>|  
|<span data-ttu-id="cb46d-535">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="cb46d-535">INTEGRATED</span></span>|<span data-ttu-id="cb46d-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="cb46d-537">Microsoft Jet OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="cb46d-537">Microsoft Jet OLE DB Provider</span></span>  

 <span data-ttu-id="cb46d-538">除了通用結構描述集合之外，Microsoft Jet OLE DB 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="cb46d-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="cb46d-539">資料表</span><span class="sxs-lookup"><span data-stu-id="cb46d-539">Tables</span></span>  
  
- <span data-ttu-id="cb46d-540">資料行</span><span class="sxs-lookup"><span data-stu-id="cb46d-540">Columns</span></span>  
  
- <span data-ttu-id="cb46d-541">程序</span><span class="sxs-lookup"><span data-stu-id="cb46d-541">Procedures</span></span>  
  
- <span data-ttu-id="cb46d-542">檢視</span><span class="sxs-lookup"><span data-stu-id="cb46d-542">Views</span></span>  
  
- <span data-ttu-id="cb46d-543">索引</span><span class="sxs-lookup"><span data-stu-id="cb46d-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="cb46d-544">資料表</span><span class="sxs-lookup"><span data-stu-id="cb46d-544">Tables</span></span>  
  
|<span data-ttu-id="cb46d-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cb46d-545">ColumnName</span></span>|<span data-ttu-id="cb46d-546">DataType</span><span class="sxs-lookup"><span data-stu-id="cb46d-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cb46d-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cb46d-547">TABLE_CATALOG</span></span>|<span data-ttu-id="cb46d-548">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-548">String</span></span>|  
|<span data-ttu-id="cb46d-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cb46d-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="cb46d-550">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-550">String</span></span>|  
|<span data-ttu-id="cb46d-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-551">TABLE_NAME</span></span>|<span data-ttu-id="cb46d-552">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-552">String</span></span>|  
|<span data-ttu-id="cb46d-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="cb46d-553">TABLE_TYPE</span></span>|<span data-ttu-id="cb46d-554">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-554">String</span></span>|  
|<span data-ttu-id="cb46d-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="cb46d-555">TABLE_GUID</span></span>|<span data-ttu-id="cb46d-556">Guid</span><span class="sxs-lookup"><span data-stu-id="cb46d-556">Guid</span></span>|  
|<span data-ttu-id="cb46d-557">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cb46d-557">DESCRIPTION</span></span>|<span data-ttu-id="cb46d-558">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-558">String</span></span>|  
|<span data-ttu-id="cb46d-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="cb46d-559">TABLE_PROPID</span></span>|<span data-ttu-id="cb46d-560">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-560">Int64</span></span>|  
|<span data-ttu-id="cb46d-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="cb46d-561">DATE_CREATED</span></span>|<span data-ttu-id="cb46d-562">Datetime</span><span class="sxs-lookup"><span data-stu-id="cb46d-562">DateTime</span></span>|  
|<span data-ttu-id="cb46d-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="cb46d-563">DATE_MODIFIED</span></span>|<span data-ttu-id="cb46d-564">Datetime</span><span class="sxs-lookup"><span data-stu-id="cb46d-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="cb46d-565">資料行</span><span class="sxs-lookup"><span data-stu-id="cb46d-565">Columns</span></span>  
  
|<span data-ttu-id="cb46d-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cb46d-566">ColumnName</span></span>|<span data-ttu-id="cb46d-567">DataType</span><span class="sxs-lookup"><span data-stu-id="cb46d-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cb46d-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cb46d-568">TABLE_CATALOG</span></span>|<span data-ttu-id="cb46d-569">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-569">String</span></span>|  
|<span data-ttu-id="cb46d-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cb46d-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="cb46d-571">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-571">String</span></span>|  
|<span data-ttu-id="cb46d-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-572">TABLE_NAME</span></span>|<span data-ttu-id="cb46d-573">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-573">String</span></span>|  
|<span data-ttu-id="cb46d-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-574">COLUMN_NAME</span></span>|<span data-ttu-id="cb46d-575">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-575">String</span></span>|  
|<span data-ttu-id="cb46d-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="cb46d-576">COLUMN_GUID</span></span>|<span data-ttu-id="cb46d-577">Guid</span><span class="sxs-lookup"><span data-stu-id="cb46d-577">Guid</span></span>|  
|<span data-ttu-id="cb46d-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="cb46d-578">COLUMN_PROPID</span></span>|<span data-ttu-id="cb46d-579">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-579">Int64</span></span>|  
|<span data-ttu-id="cb46d-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cb46d-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="cb46d-581">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-581">Int64</span></span>|  
|<span data-ttu-id="cb46d-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="cb46d-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="cb46d-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-583">Boolean</span></span>|  
|<span data-ttu-id="cb46d-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="cb46d-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="cb46d-585">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-585">String</span></span>|  
|<span data-ttu-id="cb46d-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="cb46d-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="cb46d-587">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-587">Int64</span></span>|  
|<span data-ttu-id="cb46d-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="cb46d-588">IS_NULLABLE</span></span>|<span data-ttu-id="cb46d-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-589">Boolean</span></span>|  
|<span data-ttu-id="cb46d-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="cb46d-590">DATA_TYPE</span></span>|<span data-ttu-id="cb46d-591">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-591">Int32</span></span>|  
|<span data-ttu-id="cb46d-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="cb46d-592">TYPE_GUID</span></span>|<span data-ttu-id="cb46d-593">Guid</span><span class="sxs-lookup"><span data-stu-id="cb46d-593">Guid</span></span>|  
|<span data-ttu-id="cb46d-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cb46d-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="cb46d-595">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-595">Int64</span></span>|  
|<span data-ttu-id="cb46d-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="cb46d-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="cb46d-597">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-597">Int64</span></span>|  
|<span data-ttu-id="cb46d-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="cb46d-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="cb46d-599">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-599">Int32</span></span>|  
|<span data-ttu-id="cb46d-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="cb46d-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="cb46d-601">Int16</span><span class="sxs-lookup"><span data-stu-id="cb46d-601">Int16</span></span>|  
|<span data-ttu-id="cb46d-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="cb46d-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="cb46d-603">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-603">Int64</span></span>|  
|<span data-ttu-id="cb46d-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cb46d-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="cb46d-605">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-605">String</span></span>|  
|<span data-ttu-id="cb46d-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cb46d-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="cb46d-607">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-607">String</span></span>|  
|<span data-ttu-id="cb46d-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="cb46d-609">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-609">String</span></span>|  
|<span data-ttu-id="cb46d-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cb46d-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="cb46d-611">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-611">String</span></span>|  
|<span data-ttu-id="cb46d-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cb46d-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="cb46d-613">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-613">String</span></span>|  
|<span data-ttu-id="cb46d-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-614">COLLATION_NAME</span></span>|<span data-ttu-id="cb46d-615">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-615">String</span></span>|  
|<span data-ttu-id="cb46d-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cb46d-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="cb46d-617">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-617">String</span></span>|  
|<span data-ttu-id="cb46d-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cb46d-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="cb46d-619">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-619">String</span></span>|  
|<span data-ttu-id="cb46d-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-620">DOMAIN_NAME</span></span>|<span data-ttu-id="cb46d-621">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-621">String</span></span>|  
|<span data-ttu-id="cb46d-622">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cb46d-622">DESCRIPTION</span></span>|<span data-ttu-id="cb46d-623">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="cb46d-624">程序</span><span class="sxs-lookup"><span data-stu-id="cb46d-624">Procedures</span></span>  
  
|<span data-ttu-id="cb46d-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cb46d-625">ColumnName</span></span>|<span data-ttu-id="cb46d-626">DataType</span><span class="sxs-lookup"><span data-stu-id="cb46d-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cb46d-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cb46d-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="cb46d-628">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-628">String</span></span>|  
|<span data-ttu-id="cb46d-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cb46d-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="cb46d-630">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-630">String</span></span>|  
|<span data-ttu-id="cb46d-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="cb46d-632">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-632">String</span></span>|  
|<span data-ttu-id="cb46d-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="cb46d-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="cb46d-634">Int16</span><span class="sxs-lookup"><span data-stu-id="cb46d-634">Int16</span></span>|  
|<span data-ttu-id="cb46d-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="cb46d-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="cb46d-636">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-636">String</span></span>|  
|<span data-ttu-id="cb46d-637">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cb46d-637">DESCRIPTION</span></span>|<span data-ttu-id="cb46d-638">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-638">String</span></span>|  
|<span data-ttu-id="cb46d-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="cb46d-639">DATE_CREATED</span></span>|<span data-ttu-id="cb46d-640">Datetime</span><span class="sxs-lookup"><span data-stu-id="cb46d-640">DateTime</span></span>|  
|<span data-ttu-id="cb46d-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="cb46d-641">DATE_MODIFIED</span></span>|<span data-ttu-id="cb46d-642">Datetime</span><span class="sxs-lookup"><span data-stu-id="cb46d-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="cb46d-643">檢視</span><span class="sxs-lookup"><span data-stu-id="cb46d-643">Views</span></span>  
  
|<span data-ttu-id="cb46d-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cb46d-644">ColumnName</span></span>|<span data-ttu-id="cb46d-645">DataType</span><span class="sxs-lookup"><span data-stu-id="cb46d-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cb46d-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cb46d-646">TABLE_CATALOG</span></span>|<span data-ttu-id="cb46d-647">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-647">String</span></span>|  
|<span data-ttu-id="cb46d-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cb46d-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="cb46d-649">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-649">String</span></span>|  
|<span data-ttu-id="cb46d-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-650">TABLE_NAME</span></span>|<span data-ttu-id="cb46d-651">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-651">String</span></span>|  
|<span data-ttu-id="cb46d-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="cb46d-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="cb46d-653">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-653">String</span></span>|  
|<span data-ttu-id="cb46d-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="cb46d-654">CHECK_OPTION</span></span>|<span data-ttu-id="cb46d-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-655">Boolean</span></span>|  
|<span data-ttu-id="cb46d-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="cb46d-656">IS_UPDATABLE</span></span>|<span data-ttu-id="cb46d-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-657">Boolean</span></span>|  
|<span data-ttu-id="cb46d-658">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="cb46d-658">DESCRIPTION</span></span>|<span data-ttu-id="cb46d-659">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-659">String</span></span>|  
|<span data-ttu-id="cb46d-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="cb46d-660">DATE_CREATED</span></span>|<span data-ttu-id="cb46d-661">Datetime</span><span class="sxs-lookup"><span data-stu-id="cb46d-661">DateTime</span></span>|  
|<span data-ttu-id="cb46d-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="cb46d-662">DATE_MODIFIED</span></span>|<span data-ttu-id="cb46d-663">Datetime</span><span class="sxs-lookup"><span data-stu-id="cb46d-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="cb46d-664">索引</span><span class="sxs-lookup"><span data-stu-id="cb46d-664">Indexes</span></span>  
  
|<span data-ttu-id="cb46d-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="cb46d-665">ColumnName</span></span>|<span data-ttu-id="cb46d-666">DataType</span><span class="sxs-lookup"><span data-stu-id="cb46d-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="cb46d-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cb46d-667">TABLE_CATALOG</span></span>|<span data-ttu-id="cb46d-668">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-668">String</span></span>|  
|<span data-ttu-id="cb46d-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cb46d-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="cb46d-670">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-670">String</span></span>|  
|<span data-ttu-id="cb46d-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-671">TABLE_NAME</span></span>|<span data-ttu-id="cb46d-672">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-672">String</span></span>|  
|<span data-ttu-id="cb46d-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cb46d-673">INDEX_CATALOG</span></span>|<span data-ttu-id="cb46d-674">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-674">String</span></span>|  
|<span data-ttu-id="cb46d-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cb46d-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="cb46d-676">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-676">String</span></span>|  
|<span data-ttu-id="cb46d-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-677">INDEX_NAME</span></span>|<span data-ttu-id="cb46d-678">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-678">String</span></span>|  
|<span data-ttu-id="cb46d-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="cb46d-679">PRIMARY_KEY</span></span>|<span data-ttu-id="cb46d-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-680">Boolean</span></span>|  
|<span data-ttu-id="cb46d-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="cb46d-681">UNIQUE</span></span>|<span data-ttu-id="cb46d-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-682">Boolean</span></span>|  
|<span data-ttu-id="cb46d-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="cb46d-683">CLUSTERED</span></span>|<span data-ttu-id="cb46d-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-684">Boolean</span></span>|  
|<span data-ttu-id="cb46d-685">TYPE</span><span class="sxs-lookup"><span data-stu-id="cb46d-685">TYPE</span></span>|<span data-ttu-id="cb46d-686">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-686">Int32</span></span>|  
|<span data-ttu-id="cb46d-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="cb46d-687">FILL_FACTOR</span></span>|<span data-ttu-id="cb46d-688">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-688">Int32</span></span>|  
|<span data-ttu-id="cb46d-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="cb46d-689">INITIAL_SIZE</span></span>|<span data-ttu-id="cb46d-690">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-690">Int32</span></span>|  
|<span data-ttu-id="cb46d-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="cb46d-691">NULLS</span></span>|<span data-ttu-id="cb46d-692">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-692">Int32</span></span>|  
|<span data-ttu-id="cb46d-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="cb46d-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="cb46d-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-694">Boolean</span></span>|  
|<span data-ttu-id="cb46d-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="cb46d-695">AUTO_UPDATE</span></span>|<span data-ttu-id="cb46d-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-696">Boolean</span></span>|  
|<span data-ttu-id="cb46d-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="cb46d-697">NULL_COLLATION</span></span>|<span data-ttu-id="cb46d-698">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-698">Int32</span></span>|  
|<span data-ttu-id="cb46d-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="cb46d-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="cb46d-700">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-700">Int64</span></span>|  
|<span data-ttu-id="cb46d-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cb46d-701">COLUMN_NAME</span></span>|<span data-ttu-id="cb46d-702">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-702">String</span></span>|  
|<span data-ttu-id="cb46d-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="cb46d-703">COLUMN_GUID</span></span>|<span data-ttu-id="cb46d-704">Guid</span><span class="sxs-lookup"><span data-stu-id="cb46d-704">Guid</span></span>|  
|<span data-ttu-id="cb46d-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="cb46d-705">COLUMN_PROPID</span></span>|<span data-ttu-id="cb46d-706">Int64</span><span class="sxs-lookup"><span data-stu-id="cb46d-706">Int64</span></span>|  
|<span data-ttu-id="cb46d-707">COLLATION</span><span class="sxs-lookup"><span data-stu-id="cb46d-707">COLLATION</span></span>|<span data-ttu-id="cb46d-708">Int16</span><span class="sxs-lookup"><span data-stu-id="cb46d-708">Int16</span></span>|  
|<span data-ttu-id="cb46d-709">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="cb46d-709">CARDINALITY</span></span>|<span data-ttu-id="cb46d-710">Decimal</span><span class="sxs-lookup"><span data-stu-id="cb46d-710">Decimal</span></span>|  
|<span data-ttu-id="cb46d-711">PAGES</span><span class="sxs-lookup"><span data-stu-id="cb46d-711">PAGES</span></span>|<span data-ttu-id="cb46d-712">Int32</span><span class="sxs-lookup"><span data-stu-id="cb46d-712">Int32</span></span>|  
|<span data-ttu-id="cb46d-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="cb46d-713">FILTER_CONDITION</span></span>|<span data-ttu-id="cb46d-714">String</span><span class="sxs-lookup"><span data-stu-id="cb46d-714">String</span></span>|  
|<span data-ttu-id="cb46d-715">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="cb46d-715">INTEGRATED</span></span>|<span data-ttu-id="cb46d-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="cb46d-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cb46d-717">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb46d-717">See also</span></span>

- <span data-ttu-id="cb46d-718">[ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="cb46d-718">[ADO.NET Overview](ado-net-overview.md)</span></span>
