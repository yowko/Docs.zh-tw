---
title: OLE DB 結構描述集合
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: f753f35aab0a0200da5de463a73abb9813253d11
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658451"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="74a88-102">OLE DB 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="74a88-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="74a88-103">本節將討論 Microsoft SQL Server、Oracle 和 Microsoft Jet 之 OLE DB 提供者的結構描述集合支援。</span><span class="sxs-lookup"><span data-stu-id="74a88-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="74a88-104">Microsoft SQL Server OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="74a88-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="74a88-105">Microsoft SQL Server OLE DB 驅動程式支援下列特定結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="74a88-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="74a88-106">資料表</span><span class="sxs-lookup"><span data-stu-id="74a88-106">Tables</span></span>  
  
-   <span data-ttu-id="74a88-107">資料行</span><span class="sxs-lookup"><span data-stu-id="74a88-107">Columns</span></span>  
  
-   <span data-ttu-id="74a88-108">程序</span><span class="sxs-lookup"><span data-stu-id="74a88-108">Procedures</span></span>  
  
-   <span data-ttu-id="74a88-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="74a88-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="74a88-110">Catalog</span><span class="sxs-lookup"><span data-stu-id="74a88-110">Catalog</span></span>  
  
-   <span data-ttu-id="74a88-111">Indexes</span><span class="sxs-lookup"><span data-stu-id="74a88-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="74a88-112">資料表</span><span class="sxs-lookup"><span data-stu-id="74a88-112">Tables</span></span>  
  
|<span data-ttu-id="74a88-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="74a88-113">ColumnName</span></span>|<span data-ttu-id="74a88-114">DataType</span><span class="sxs-lookup"><span data-stu-id="74a88-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="74a88-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="74a88-115">TABLE_CATALOG</span></span>|<span data-ttu-id="74a88-116">String</span><span class="sxs-lookup"><span data-stu-id="74a88-116">String</span></span>|  
|<span data-ttu-id="74a88-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="74a88-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="74a88-118">String</span><span class="sxs-lookup"><span data-stu-id="74a88-118">String</span></span>|  
|<span data-ttu-id="74a88-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-119">TABLE_NAME</span></span>|<span data-ttu-id="74a88-120">String</span><span class="sxs-lookup"><span data-stu-id="74a88-120">String</span></span>|  
|<span data-ttu-id="74a88-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="74a88-121">TABLE_TYPE</span></span>|<span data-ttu-id="74a88-122">String</span><span class="sxs-lookup"><span data-stu-id="74a88-122">String</span></span>|  
|<span data-ttu-id="74a88-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="74a88-123">TABLE_GUID</span></span>|<span data-ttu-id="74a88-124">Guid</span><span class="sxs-lookup"><span data-stu-id="74a88-124">Guid</span></span>|  
|<span data-ttu-id="74a88-125">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="74a88-125">DESCRIPTION</span></span>|<span data-ttu-id="74a88-126">String</span><span class="sxs-lookup"><span data-stu-id="74a88-126">String</span></span>|  
|<span data-ttu-id="74a88-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="74a88-127">TABLE_PROPID</span></span>|<span data-ttu-id="74a88-128">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-128">Int64</span></span>|  
|<span data-ttu-id="74a88-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="74a88-129">DATE_CREATED</span></span>|<span data-ttu-id="74a88-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="74a88-130">DateTime</span></span>|  
|<span data-ttu-id="74a88-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="74a88-131">DATE_MODIFIED</span></span>|<span data-ttu-id="74a88-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="74a88-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="74a88-133">資料行</span><span class="sxs-lookup"><span data-stu-id="74a88-133">Columns</span></span>  
  
|<span data-ttu-id="74a88-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="74a88-134">ColumnName</span></span>|<span data-ttu-id="74a88-135">DataType</span><span class="sxs-lookup"><span data-stu-id="74a88-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="74a88-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="74a88-136">TABLE_CATALOG</span></span>|<span data-ttu-id="74a88-137">String</span><span class="sxs-lookup"><span data-stu-id="74a88-137">String</span></span>|  
|<span data-ttu-id="74a88-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="74a88-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="74a88-139">String</span><span class="sxs-lookup"><span data-stu-id="74a88-139">String</span></span>|  
|<span data-ttu-id="74a88-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-140">TABLE_NAME</span></span>|<span data-ttu-id="74a88-141">String</span><span class="sxs-lookup"><span data-stu-id="74a88-141">String</span></span>|  
|<span data-ttu-id="74a88-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-142">COLUMN_NAME</span></span>|<span data-ttu-id="74a88-143">String</span><span class="sxs-lookup"><span data-stu-id="74a88-143">String</span></span>|  
|<span data-ttu-id="74a88-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="74a88-144">COLUMN_GUID</span></span>|<span data-ttu-id="74a88-145">Guid</span><span class="sxs-lookup"><span data-stu-id="74a88-145">Guid</span></span>|  
|<span data-ttu-id="74a88-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="74a88-146">COLUMN_PROPID</span></span>|<span data-ttu-id="74a88-147">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-147">Int64</span></span>|  
|<span data-ttu-id="74a88-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="74a88-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="74a88-149">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-149">Int64</span></span>|  
|<span data-ttu-id="74a88-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="74a88-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="74a88-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-151">Boolean</span></span>|  
|<span data-ttu-id="74a88-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="74a88-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="74a88-153">String</span><span class="sxs-lookup"><span data-stu-id="74a88-153">String</span></span>|  
|<span data-ttu-id="74a88-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="74a88-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="74a88-155">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-155">Int64</span></span>|  
|<span data-ttu-id="74a88-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="74a88-156">IS_NULLABLE</span></span>|<span data-ttu-id="74a88-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-157">Boolean</span></span>|  
|<span data-ttu-id="74a88-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="74a88-158">DATA_TYPE</span></span>|<span data-ttu-id="74a88-159">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-159">Int32</span></span>|  
|<span data-ttu-id="74a88-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="74a88-160">TYPE_GUID</span></span>|<span data-ttu-id="74a88-161">Guid</span><span class="sxs-lookup"><span data-stu-id="74a88-161">Guid</span></span>|  
|<span data-ttu-id="74a88-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="74a88-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="74a88-163">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-163">Int64</span></span>|  
|<span data-ttu-id="74a88-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="74a88-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="74a88-165">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-165">Int64</span></span>|  
|<span data-ttu-id="74a88-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="74a88-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="74a88-167">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-167">Int32</span></span>|  
|<span data-ttu-id="74a88-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="74a88-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="74a88-169">Int16</span><span class="sxs-lookup"><span data-stu-id="74a88-169">Int16</span></span>|  
|<span data-ttu-id="74a88-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="74a88-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="74a88-171">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-171">Int64</span></span>|  
|<span data-ttu-id="74a88-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="74a88-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="74a88-173">String</span><span class="sxs-lookup"><span data-stu-id="74a88-173">String</span></span>|  
|<span data-ttu-id="74a88-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="74a88-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="74a88-175">String</span><span class="sxs-lookup"><span data-stu-id="74a88-175">String</span></span>|  
|<span data-ttu-id="74a88-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="74a88-177">String</span><span class="sxs-lookup"><span data-stu-id="74a88-177">String</span></span>|  
|<span data-ttu-id="74a88-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="74a88-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="74a88-179">String</span><span class="sxs-lookup"><span data-stu-id="74a88-179">String</span></span>|  
|<span data-ttu-id="74a88-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="74a88-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="74a88-181">String</span><span class="sxs-lookup"><span data-stu-id="74a88-181">String</span></span>|  
|<span data-ttu-id="74a88-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-182">COLLATION_NAME</span></span>|<span data-ttu-id="74a88-183">String</span><span class="sxs-lookup"><span data-stu-id="74a88-183">String</span></span>|  
|<span data-ttu-id="74a88-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="74a88-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="74a88-185">String</span><span class="sxs-lookup"><span data-stu-id="74a88-185">String</span></span>|  
|<span data-ttu-id="74a88-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="74a88-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="74a88-187">String</span><span class="sxs-lookup"><span data-stu-id="74a88-187">String</span></span>|  
|<span data-ttu-id="74a88-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-188">DOMAIN_NAME</span></span>|<span data-ttu-id="74a88-189">String</span><span class="sxs-lookup"><span data-stu-id="74a88-189">String</span></span>|  
|<span data-ttu-id="74a88-190">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="74a88-190">DESCRIPTION</span></span>|<span data-ttu-id="74a88-191">String</span><span class="sxs-lookup"><span data-stu-id="74a88-191">String</span></span>|  
|<span data-ttu-id="74a88-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="74a88-192">COLUMN_LCID</span></span>|<span data-ttu-id="74a88-193">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-193">Int32</span></span>|  
|<span data-ttu-id="74a88-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="74a88-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="74a88-195">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-195">Int32</span></span>|  
|<span data-ttu-id="74a88-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="74a88-196">COLUMN_SORTID</span></span>|<span data-ttu-id="74a88-197">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-197">Int32</span></span>|  
|<span data-ttu-id="74a88-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="74a88-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="74a88-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="74a88-199">Byte[]</span></span>|  
|<span data-ttu-id="74a88-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="74a88-200">IS_COMPUTED</span></span>|<span data-ttu-id="74a88-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="74a88-202">程序</span><span class="sxs-lookup"><span data-stu-id="74a88-202">Procedures</span></span>  
  
|<span data-ttu-id="74a88-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="74a88-203">ColumnName</span></span>|<span data-ttu-id="74a88-204">DataType</span><span class="sxs-lookup"><span data-stu-id="74a88-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="74a88-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="74a88-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="74a88-206">String</span><span class="sxs-lookup"><span data-stu-id="74a88-206">String</span></span>|  
|<span data-ttu-id="74a88-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="74a88-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="74a88-208">String</span><span class="sxs-lookup"><span data-stu-id="74a88-208">String</span></span>|  
|<span data-ttu-id="74a88-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="74a88-210">String</span><span class="sxs-lookup"><span data-stu-id="74a88-210">String</span></span>|  
|<span data-ttu-id="74a88-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="74a88-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="74a88-212">Int16</span><span class="sxs-lookup"><span data-stu-id="74a88-212">Int16</span></span>|  
|<span data-ttu-id="74a88-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="74a88-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="74a88-214">String</span><span class="sxs-lookup"><span data-stu-id="74a88-214">String</span></span>|  
|<span data-ttu-id="74a88-215">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="74a88-215">DESCRIPTION</span></span>|<span data-ttu-id="74a88-216">String</span><span class="sxs-lookup"><span data-stu-id="74a88-216">String</span></span>|  
|<span data-ttu-id="74a88-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="74a88-217">DATE_CREATED</span></span>|<span data-ttu-id="74a88-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="74a88-218">DateTime</span></span>|  
|<span data-ttu-id="74a88-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="74a88-219">DATE_MODIFIED</span></span>|<span data-ttu-id="74a88-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="74a88-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="74a88-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="74a88-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="74a88-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="74a88-222">ColumnName</span></span>|<span data-ttu-id="74a88-223">DataType</span><span class="sxs-lookup"><span data-stu-id="74a88-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="74a88-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="74a88-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="74a88-225">String</span><span class="sxs-lookup"><span data-stu-id="74a88-225">String</span></span>|  
|<span data-ttu-id="74a88-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="74a88-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="74a88-227">String</span><span class="sxs-lookup"><span data-stu-id="74a88-227">String</span></span>|  
|<span data-ttu-id="74a88-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="74a88-229">String</span><span class="sxs-lookup"><span data-stu-id="74a88-229">String</span></span>|  
|<span data-ttu-id="74a88-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-230">PARAMETER_NAME</span></span>|<span data-ttu-id="74a88-231">String</span><span class="sxs-lookup"><span data-stu-id="74a88-231">String</span></span>|  
|<span data-ttu-id="74a88-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="74a88-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="74a88-233">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-233">Int32</span></span>|  
|<span data-ttu-id="74a88-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="74a88-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="74a88-235">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-235">Int32</span></span>|  
|<span data-ttu-id="74a88-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="74a88-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="74a88-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-237">Boolean</span></span>|  
|<span data-ttu-id="74a88-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="74a88-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="74a88-239">String</span><span class="sxs-lookup"><span data-stu-id="74a88-239">String</span></span>|  
|<span data-ttu-id="74a88-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="74a88-240">IS_NULLABLE</span></span>|<span data-ttu-id="74a88-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-241">Boolean</span></span>|  
|<span data-ttu-id="74a88-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="74a88-242">DATA_TYPE</span></span>|<span data-ttu-id="74a88-243">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-243">Int32</span></span>|  
|<span data-ttu-id="74a88-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="74a88-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="74a88-245">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-245">Int64</span></span>|  
|<span data-ttu-id="74a88-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="74a88-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="74a88-247">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-247">Int64</span></span>|  
|<span data-ttu-id="74a88-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="74a88-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="74a88-249">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-249">Int32</span></span>|  
|<span data-ttu-id="74a88-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="74a88-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="74a88-251">Int16</span><span class="sxs-lookup"><span data-stu-id="74a88-251">Int16</span></span>|  
|<span data-ttu-id="74a88-252">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="74a88-252">DESCRIPTION</span></span>|<span data-ttu-id="74a88-253">String</span><span class="sxs-lookup"><span data-stu-id="74a88-253">String</span></span>|  
|<span data-ttu-id="74a88-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-254">TYPE_NAME</span></span>|<span data-ttu-id="74a88-255">String</span><span class="sxs-lookup"><span data-stu-id="74a88-255">String</span></span>|  
|<span data-ttu-id="74a88-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="74a88-257">String</span><span class="sxs-lookup"><span data-stu-id="74a88-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="74a88-258">Catalog</span><span class="sxs-lookup"><span data-stu-id="74a88-258">Catalog</span></span>  
  
|<span data-ttu-id="74a88-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="74a88-259">ColumnName</span></span>|<span data-ttu-id="74a88-260">DataType</span><span class="sxs-lookup"><span data-stu-id="74a88-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="74a88-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-261">CATALOG_NAME</span></span>|<span data-ttu-id="74a88-262">String</span><span class="sxs-lookup"><span data-stu-id="74a88-262">String</span></span>|  
|<span data-ttu-id="74a88-263">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="74a88-263">DESCRIPTION</span></span>|<span data-ttu-id="74a88-264">String</span><span class="sxs-lookup"><span data-stu-id="74a88-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="74a88-265">Indexes</span><span class="sxs-lookup"><span data-stu-id="74a88-265">Indexes</span></span>  
  
|<span data-ttu-id="74a88-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="74a88-266">ColumnName</span></span>|<span data-ttu-id="74a88-267">DataType</span><span class="sxs-lookup"><span data-stu-id="74a88-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="74a88-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="74a88-268">TABLE_CATALOG</span></span>|<span data-ttu-id="74a88-269">String</span><span class="sxs-lookup"><span data-stu-id="74a88-269">String</span></span>|  
|<span data-ttu-id="74a88-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="74a88-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="74a88-271">String</span><span class="sxs-lookup"><span data-stu-id="74a88-271">String</span></span>|  
|<span data-ttu-id="74a88-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-272">TABLE_NAME</span></span>|<span data-ttu-id="74a88-273">String</span><span class="sxs-lookup"><span data-stu-id="74a88-273">String</span></span>|  
|<span data-ttu-id="74a88-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="74a88-274">INDEX_CATALOG</span></span>|<span data-ttu-id="74a88-275">String</span><span class="sxs-lookup"><span data-stu-id="74a88-275">String</span></span>|  
|<span data-ttu-id="74a88-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="74a88-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="74a88-277">String</span><span class="sxs-lookup"><span data-stu-id="74a88-277">String</span></span>|  
|<span data-ttu-id="74a88-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-278">INDEX_NAME</span></span>|<span data-ttu-id="74a88-279">String</span><span class="sxs-lookup"><span data-stu-id="74a88-279">String</span></span>|  
|<span data-ttu-id="74a88-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="74a88-280">PRIMARY_KEY</span></span>|<span data-ttu-id="74a88-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-281">Boolean</span></span>|  
|<span data-ttu-id="74a88-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="74a88-282">UNIQUE</span></span>|<span data-ttu-id="74a88-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-283">Boolean</span></span>|  
|<span data-ttu-id="74a88-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="74a88-284">CLUSTERED</span></span>|<span data-ttu-id="74a88-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-285">Boolean</span></span>|  
|<span data-ttu-id="74a88-286">TYPE</span><span class="sxs-lookup"><span data-stu-id="74a88-286">TYPE</span></span>|<span data-ttu-id="74a88-287">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-287">Int32</span></span>|  
|<span data-ttu-id="74a88-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="74a88-288">FILL_FACTOR</span></span>|<span data-ttu-id="74a88-289">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-289">Int32</span></span>|  
|<span data-ttu-id="74a88-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="74a88-290">INITIAL_SIZE</span></span>|<span data-ttu-id="74a88-291">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-291">Int32</span></span>|  
|<span data-ttu-id="74a88-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="74a88-292">NULLS</span></span>|<span data-ttu-id="74a88-293">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-293">Int32</span></span>|  
|<span data-ttu-id="74a88-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="74a88-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="74a88-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-295">Boolean</span></span>|  
|<span data-ttu-id="74a88-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="74a88-296">AUTO_UPDATE</span></span>|<span data-ttu-id="74a88-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-297">Boolean</span></span>|  
|<span data-ttu-id="74a88-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="74a88-298">NULL_COLLATION</span></span>|<span data-ttu-id="74a88-299">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-299">Int32</span></span>|  
|<span data-ttu-id="74a88-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="74a88-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="74a88-301">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-301">Int64</span></span>|  
|<span data-ttu-id="74a88-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-302">COLUMN_NAME</span></span>|<span data-ttu-id="74a88-303">String</span><span class="sxs-lookup"><span data-stu-id="74a88-303">String</span></span>|  
|<span data-ttu-id="74a88-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="74a88-304">COLUMN_GUID</span></span>|<span data-ttu-id="74a88-305">Guid</span><span class="sxs-lookup"><span data-stu-id="74a88-305">Guid</span></span>|  
|<span data-ttu-id="74a88-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="74a88-306">COLUMN_PROPID</span></span>|<span data-ttu-id="74a88-307">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-307">Int64</span></span>|  
|<span data-ttu-id="74a88-308">COLLATION</span><span class="sxs-lookup"><span data-stu-id="74a88-308">COLLATION</span></span>|<span data-ttu-id="74a88-309">Int16</span><span class="sxs-lookup"><span data-stu-id="74a88-309">Int16</span></span>|  
|<span data-ttu-id="74a88-310">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="74a88-310">CARDINALITY</span></span>|<span data-ttu-id="74a88-311">Decimal</span><span class="sxs-lookup"><span data-stu-id="74a88-311">Decimal</span></span>|  
|<span data-ttu-id="74a88-312">PAGES</span><span class="sxs-lookup"><span data-stu-id="74a88-312">PAGES</span></span>|<span data-ttu-id="74a88-313">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-313">Int32</span></span>|  
|<span data-ttu-id="74a88-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="74a88-314">FILTER_CONDITION</span></span>|<span data-ttu-id="74a88-315">String</span><span class="sxs-lookup"><span data-stu-id="74a88-315">String</span></span>|  
|<span data-ttu-id="74a88-316">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="74a88-316">INTEGRATED</span></span>|<span data-ttu-id="74a88-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="74a88-318">Microsoft Oracle OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="74a88-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="74a88-319">除了通用結構描述集合之外，Microsoft Oracle OLE DB 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="74a88-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="74a88-320">資料表</span><span class="sxs-lookup"><span data-stu-id="74a88-320">Tables</span></span>  
  
-   <span data-ttu-id="74a88-321">資料行</span><span class="sxs-lookup"><span data-stu-id="74a88-321">Columns</span></span>  
  
-   <span data-ttu-id="74a88-322">程序</span><span class="sxs-lookup"><span data-stu-id="74a88-322">Procedures</span></span>  
  
-   <span data-ttu-id="74a88-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="74a88-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="74a88-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="74a88-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="74a88-325">檢視</span><span class="sxs-lookup"><span data-stu-id="74a88-325">Views</span></span>  
  
-   <span data-ttu-id="74a88-326">Indexes</span><span class="sxs-lookup"><span data-stu-id="74a88-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="74a88-327">資料表</span><span class="sxs-lookup"><span data-stu-id="74a88-327">Tables</span></span>  
  
|<span data-ttu-id="74a88-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="74a88-328">ColumnName</span></span>|<span data-ttu-id="74a88-329">DataType</span><span class="sxs-lookup"><span data-stu-id="74a88-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="74a88-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="74a88-330">TABLE_CATALOG</span></span>|<span data-ttu-id="74a88-331">String</span><span class="sxs-lookup"><span data-stu-id="74a88-331">String</span></span>|  
|<span data-ttu-id="74a88-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="74a88-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="74a88-333">String</span><span class="sxs-lookup"><span data-stu-id="74a88-333">String</span></span>|  
|<span data-ttu-id="74a88-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-334">TABLE_NAME</span></span>|<span data-ttu-id="74a88-335">String</span><span class="sxs-lookup"><span data-stu-id="74a88-335">String</span></span>|  
|<span data-ttu-id="74a88-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="74a88-336">TABLE_TYPE</span></span>|<span data-ttu-id="74a88-337">String</span><span class="sxs-lookup"><span data-stu-id="74a88-337">String</span></span>|  
|<span data-ttu-id="74a88-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="74a88-338">TABLE_GUID</span></span>|<span data-ttu-id="74a88-339">Guid</span><span class="sxs-lookup"><span data-stu-id="74a88-339">Guid</span></span>|  
|<span data-ttu-id="74a88-340">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="74a88-340">DESCRIPTION</span></span>|<span data-ttu-id="74a88-341">String</span><span class="sxs-lookup"><span data-stu-id="74a88-341">String</span></span>|  
|<span data-ttu-id="74a88-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="74a88-342">TABLE_PROPID</span></span>|<span data-ttu-id="74a88-343">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-343">Int64</span></span>|  
|<span data-ttu-id="74a88-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="74a88-344">DATE_CREATED</span></span>|<span data-ttu-id="74a88-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="74a88-345">DateTime</span></span>|  
|<span data-ttu-id="74a88-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="74a88-346">DATE_MODIFIED</span></span>|<span data-ttu-id="74a88-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="74a88-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="74a88-348">資料行</span><span class="sxs-lookup"><span data-stu-id="74a88-348">Columns</span></span>  
  
|<span data-ttu-id="74a88-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="74a88-349">ColumnName</span></span>|<span data-ttu-id="74a88-350">DataType</span><span class="sxs-lookup"><span data-stu-id="74a88-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="74a88-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="74a88-351">TABLE_CATALOG</span></span>|<span data-ttu-id="74a88-352">String</span><span class="sxs-lookup"><span data-stu-id="74a88-352">String</span></span>|  
|<span data-ttu-id="74a88-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="74a88-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="74a88-354">String</span><span class="sxs-lookup"><span data-stu-id="74a88-354">String</span></span>|  
|<span data-ttu-id="74a88-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-355">TABLE_NAME</span></span>|<span data-ttu-id="74a88-356">String</span><span class="sxs-lookup"><span data-stu-id="74a88-356">String</span></span>|  
|<span data-ttu-id="74a88-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-357">COLUMN_NAME</span></span>|<span data-ttu-id="74a88-358">String</span><span class="sxs-lookup"><span data-stu-id="74a88-358">String</span></span>|  
|<span data-ttu-id="74a88-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="74a88-359">COLUMN_GUID</span></span>|<span data-ttu-id="74a88-360">Guid</span><span class="sxs-lookup"><span data-stu-id="74a88-360">Guid</span></span>|  
|<span data-ttu-id="74a88-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="74a88-361">COLUMN_PROPID</span></span>|<span data-ttu-id="74a88-362">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-362">Int64</span></span>|  
|<span data-ttu-id="74a88-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="74a88-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="74a88-364">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-364">Int64</span></span>|  
|<span data-ttu-id="74a88-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="74a88-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="74a88-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-366">Boolean</span></span>|  
|<span data-ttu-id="74a88-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="74a88-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="74a88-368">String</span><span class="sxs-lookup"><span data-stu-id="74a88-368">String</span></span>|  
|<span data-ttu-id="74a88-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="74a88-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="74a88-370">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-370">Int64</span></span>|  
|<span data-ttu-id="74a88-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="74a88-371">IS_NULLABLE</span></span>|<span data-ttu-id="74a88-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-372">Boolean</span></span>|  
|<span data-ttu-id="74a88-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="74a88-373">DATA_TYPE</span></span>|<span data-ttu-id="74a88-374">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-374">Int32</span></span>|  
|<span data-ttu-id="74a88-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="74a88-375">TYPE_GUID</span></span>|<span data-ttu-id="74a88-376">Guid</span><span class="sxs-lookup"><span data-stu-id="74a88-376">Guid</span></span>|  
|<span data-ttu-id="74a88-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="74a88-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="74a88-378">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-378">Int64</span></span>|  
|<span data-ttu-id="74a88-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="74a88-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="74a88-380">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-380">Int64</span></span>|  
|<span data-ttu-id="74a88-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="74a88-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="74a88-382">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-382">Int32</span></span>|  
|<span data-ttu-id="74a88-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="74a88-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="74a88-384">Int16</span><span class="sxs-lookup"><span data-stu-id="74a88-384">Int16</span></span>|  
|<span data-ttu-id="74a88-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="74a88-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="74a88-386">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-386">Int64</span></span>|  
|<span data-ttu-id="74a88-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="74a88-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="74a88-388">String</span><span class="sxs-lookup"><span data-stu-id="74a88-388">String</span></span>|  
|<span data-ttu-id="74a88-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="74a88-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="74a88-390">String</span><span class="sxs-lookup"><span data-stu-id="74a88-390">String</span></span>|  
|<span data-ttu-id="74a88-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="74a88-392">String</span><span class="sxs-lookup"><span data-stu-id="74a88-392">String</span></span>|  
|<span data-ttu-id="74a88-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="74a88-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="74a88-394">String</span><span class="sxs-lookup"><span data-stu-id="74a88-394">String</span></span>|  
|<span data-ttu-id="74a88-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="74a88-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="74a88-396">String</span><span class="sxs-lookup"><span data-stu-id="74a88-396">String</span></span>|  
|<span data-ttu-id="74a88-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-397">COLLATION_NAME</span></span>|<span data-ttu-id="74a88-398">String</span><span class="sxs-lookup"><span data-stu-id="74a88-398">String</span></span>|  
|<span data-ttu-id="74a88-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="74a88-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="74a88-400">String</span><span class="sxs-lookup"><span data-stu-id="74a88-400">String</span></span>|  
|<span data-ttu-id="74a88-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="74a88-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="74a88-402">String</span><span class="sxs-lookup"><span data-stu-id="74a88-402">String</span></span>|  
|<span data-ttu-id="74a88-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-403">DOMAIN_NAME</span></span>|<span data-ttu-id="74a88-404">String</span><span class="sxs-lookup"><span data-stu-id="74a88-404">String</span></span>|  
|<span data-ttu-id="74a88-405">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="74a88-405">DESCRIPTION</span></span>|<span data-ttu-id="74a88-406">String</span><span class="sxs-lookup"><span data-stu-id="74a88-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="74a88-407">程序</span><span class="sxs-lookup"><span data-stu-id="74a88-407">Procedures</span></span>  
  
|<span data-ttu-id="74a88-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="74a88-408">ColumnName</span></span>|<span data-ttu-id="74a88-409">DataType</span><span class="sxs-lookup"><span data-stu-id="74a88-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="74a88-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="74a88-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="74a88-411">String</span><span class="sxs-lookup"><span data-stu-id="74a88-411">String</span></span>|  
|<span data-ttu-id="74a88-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="74a88-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="74a88-413">String</span><span class="sxs-lookup"><span data-stu-id="74a88-413">String</span></span>|  
|<span data-ttu-id="74a88-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="74a88-415">String</span><span class="sxs-lookup"><span data-stu-id="74a88-415">String</span></span>|  
|<span data-ttu-id="74a88-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="74a88-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="74a88-417">Int16</span><span class="sxs-lookup"><span data-stu-id="74a88-417">Int16</span></span>|  
|<span data-ttu-id="74a88-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="74a88-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="74a88-419">String</span><span class="sxs-lookup"><span data-stu-id="74a88-419">String</span></span>|  
|<span data-ttu-id="74a88-420">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="74a88-420">DESCRIPTION</span></span>|<span data-ttu-id="74a88-421">String</span><span class="sxs-lookup"><span data-stu-id="74a88-421">String</span></span>|  
|<span data-ttu-id="74a88-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="74a88-422">DATE_CREATED</span></span>|<span data-ttu-id="74a88-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="74a88-423">DateTime</span></span>|  
|<span data-ttu-id="74a88-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="74a88-424">DATE_MODIFIED</span></span>|<span data-ttu-id="74a88-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="74a88-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="74a88-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="74a88-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="74a88-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="74a88-427">ColumnName</span></span>|<span data-ttu-id="74a88-428">DataType</span><span class="sxs-lookup"><span data-stu-id="74a88-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="74a88-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="74a88-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="74a88-430">String</span><span class="sxs-lookup"><span data-stu-id="74a88-430">String</span></span>|  
|<span data-ttu-id="74a88-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="74a88-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="74a88-432">String</span><span class="sxs-lookup"><span data-stu-id="74a88-432">String</span></span>|  
|<span data-ttu-id="74a88-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="74a88-434">String</span><span class="sxs-lookup"><span data-stu-id="74a88-434">String</span></span>|  
|<span data-ttu-id="74a88-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-435">COLUMN_NAME</span></span>|<span data-ttu-id="74a88-436">String</span><span class="sxs-lookup"><span data-stu-id="74a88-436">String</span></span>|  
|<span data-ttu-id="74a88-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="74a88-437">COLUMN_GUID</span></span>|<span data-ttu-id="74a88-438">Guid</span><span class="sxs-lookup"><span data-stu-id="74a88-438">Guid</span></span>|  
|<span data-ttu-id="74a88-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="74a88-439">COLUMN_PROPID</span></span>|<span data-ttu-id="74a88-440">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-440">Int64</span></span>|  
|<span data-ttu-id="74a88-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="74a88-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="74a88-442">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-442">Int64</span></span>|  
|<span data-ttu-id="74a88-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="74a88-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="74a88-444">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-444">Int64</span></span>|  
|<span data-ttu-id="74a88-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="74a88-445">IS_NULLABLE</span></span>|<span data-ttu-id="74a88-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-446">Boolean</span></span>|  
|<span data-ttu-id="74a88-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="74a88-447">DATA_TYPE</span></span>|<span data-ttu-id="74a88-448">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-448">Int32</span></span>|  
|<span data-ttu-id="74a88-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="74a88-449">TYPE_GUID</span></span>|<span data-ttu-id="74a88-450">Guid</span><span class="sxs-lookup"><span data-stu-id="74a88-450">Guid</span></span>|  
|<span data-ttu-id="74a88-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="74a88-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="74a88-452">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-452">Int64</span></span>|  
|<span data-ttu-id="74a88-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="74a88-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="74a88-454">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-454">Int64</span></span>|  
|<span data-ttu-id="74a88-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="74a88-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="74a88-456">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-456">Int32</span></span>|  
|<span data-ttu-id="74a88-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="74a88-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="74a88-458">Int16</span><span class="sxs-lookup"><span data-stu-id="74a88-458">Int16</span></span>|  
|<span data-ttu-id="74a88-459">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="74a88-459">DESCRIPTION</span></span>|<span data-ttu-id="74a88-460">String</span><span class="sxs-lookup"><span data-stu-id="74a88-460">String</span></span>|  
|<span data-ttu-id="74a88-461">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="74a88-461">OVERLOAD</span></span>|<span data-ttu-id="74a88-462">Int16</span><span class="sxs-lookup"><span data-stu-id="74a88-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="74a88-463">檢視</span><span class="sxs-lookup"><span data-stu-id="74a88-463">Views</span></span>  
  
|<span data-ttu-id="74a88-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="74a88-464">ColumnName</span></span>|<span data-ttu-id="74a88-465">DataType</span><span class="sxs-lookup"><span data-stu-id="74a88-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="74a88-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="74a88-466">TABLE_CATALOG</span></span>|<span data-ttu-id="74a88-467">String</span><span class="sxs-lookup"><span data-stu-id="74a88-467">String</span></span>|  
|<span data-ttu-id="74a88-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="74a88-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="74a88-469">String</span><span class="sxs-lookup"><span data-stu-id="74a88-469">String</span></span>|  
|<span data-ttu-id="74a88-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-470">TABLE_NAME</span></span>|<span data-ttu-id="74a88-471">String</span><span class="sxs-lookup"><span data-stu-id="74a88-471">String</span></span>|  
|<span data-ttu-id="74a88-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="74a88-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="74a88-473">String</span><span class="sxs-lookup"><span data-stu-id="74a88-473">String</span></span>|  
|<span data-ttu-id="74a88-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="74a88-474">CHECK_OPTION</span></span>|<span data-ttu-id="74a88-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-475">Boolean</span></span>|  
|<span data-ttu-id="74a88-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="74a88-476">IS_UPDATABLE</span></span>|<span data-ttu-id="74a88-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-477">Boolean</span></span>|  
|<span data-ttu-id="74a88-478">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="74a88-478">DESCRIPTION</span></span>|<span data-ttu-id="74a88-479">String</span><span class="sxs-lookup"><span data-stu-id="74a88-479">String</span></span>|  
|<span data-ttu-id="74a88-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="74a88-480">DATE_CREATED</span></span>|<span data-ttu-id="74a88-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="74a88-481">DateTime</span></span>|  
|<span data-ttu-id="74a88-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="74a88-482">DATE_MODIFIED</span></span>|<span data-ttu-id="74a88-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="74a88-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="74a88-484">Indexes</span><span class="sxs-lookup"><span data-stu-id="74a88-484">Indexes</span></span>  
  
|<span data-ttu-id="74a88-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="74a88-485">ColumnName</span></span>|<span data-ttu-id="74a88-486">DataType</span><span class="sxs-lookup"><span data-stu-id="74a88-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="74a88-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="74a88-487">TABLE_CATALOG</span></span>|<span data-ttu-id="74a88-488">String</span><span class="sxs-lookup"><span data-stu-id="74a88-488">String</span></span>|  
|<span data-ttu-id="74a88-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="74a88-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="74a88-490">String</span><span class="sxs-lookup"><span data-stu-id="74a88-490">String</span></span>|  
|<span data-ttu-id="74a88-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-491">TABLE_NAME</span></span>|<span data-ttu-id="74a88-492">String</span><span class="sxs-lookup"><span data-stu-id="74a88-492">String</span></span>|  
|<span data-ttu-id="74a88-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="74a88-493">INDEX_CATALOG</span></span>|<span data-ttu-id="74a88-494">String</span><span class="sxs-lookup"><span data-stu-id="74a88-494">String</span></span>|  
|<span data-ttu-id="74a88-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="74a88-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="74a88-496">String</span><span class="sxs-lookup"><span data-stu-id="74a88-496">String</span></span>|  
|<span data-ttu-id="74a88-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-497">INDEX_NAME</span></span>|<span data-ttu-id="74a88-498">String</span><span class="sxs-lookup"><span data-stu-id="74a88-498">String</span></span>|  
|<span data-ttu-id="74a88-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="74a88-499">PRIMARY_KEY</span></span>|<span data-ttu-id="74a88-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-500">Boolean</span></span>|  
|<span data-ttu-id="74a88-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="74a88-501">UNIQUE</span></span>|<span data-ttu-id="74a88-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-502">Boolean</span></span>|  
|<span data-ttu-id="74a88-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="74a88-503">CLUSTERED</span></span>|<span data-ttu-id="74a88-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-504">Boolean</span></span>|  
|<span data-ttu-id="74a88-505">TYPE</span><span class="sxs-lookup"><span data-stu-id="74a88-505">TYPE</span></span>|<span data-ttu-id="74a88-506">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-506">Int32</span></span>|  
|<span data-ttu-id="74a88-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="74a88-507">FILL_FACTOR</span></span>|<span data-ttu-id="74a88-508">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-508">Int32</span></span>|  
|<span data-ttu-id="74a88-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="74a88-509">INITIAL_SIZE</span></span>|<span data-ttu-id="74a88-510">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-510">Int32</span></span>|  
|<span data-ttu-id="74a88-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="74a88-511">NULLS</span></span>|<span data-ttu-id="74a88-512">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-512">Int32</span></span>|  
|<span data-ttu-id="74a88-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="74a88-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="74a88-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-514">Boolean</span></span>|  
|<span data-ttu-id="74a88-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="74a88-515">AUTO_UPDATE</span></span>|<span data-ttu-id="74a88-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-516">Boolean</span></span>|  
|<span data-ttu-id="74a88-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="74a88-517">NULL_COLLATION</span></span>|<span data-ttu-id="74a88-518">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-518">Int32</span></span>|  
|<span data-ttu-id="74a88-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="74a88-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="74a88-520">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-520">Int64</span></span>|  
|<span data-ttu-id="74a88-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-521">COLUMN_NAME</span></span>|<span data-ttu-id="74a88-522">String</span><span class="sxs-lookup"><span data-stu-id="74a88-522">String</span></span>|  
|<span data-ttu-id="74a88-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="74a88-523">COLUMN_GUID</span></span>|<span data-ttu-id="74a88-524">Guid</span><span class="sxs-lookup"><span data-stu-id="74a88-524">Guid</span></span>|  
|<span data-ttu-id="74a88-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="74a88-525">COLUMN_PROPID</span></span>|<span data-ttu-id="74a88-526">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-526">Int64</span></span>|  
|<span data-ttu-id="74a88-527">COLLATION</span><span class="sxs-lookup"><span data-stu-id="74a88-527">COLLATION</span></span>|<span data-ttu-id="74a88-528">Int16</span><span class="sxs-lookup"><span data-stu-id="74a88-528">Int16</span></span>|  
|<span data-ttu-id="74a88-529">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="74a88-529">CARDINALITY</span></span>|<span data-ttu-id="74a88-530">Decimal</span><span class="sxs-lookup"><span data-stu-id="74a88-530">Decimal</span></span>|  
|<span data-ttu-id="74a88-531">PAGES</span><span class="sxs-lookup"><span data-stu-id="74a88-531">PAGES</span></span>|<span data-ttu-id="74a88-532">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-532">Int32</span></span>|  
|<span data-ttu-id="74a88-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="74a88-533">FILTER_CONDITION</span></span>|<span data-ttu-id="74a88-534">String</span><span class="sxs-lookup"><span data-stu-id="74a88-534">String</span></span>|  
|<span data-ttu-id="74a88-535">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="74a88-535">INTEGRATED</span></span>|<span data-ttu-id="74a88-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="74a88-537">Microsoft Jet OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="74a88-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="74a88-538">除了通用結構描述集合之外，Microsoft Jet OLE DB 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="74a88-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="74a88-539">資料表</span><span class="sxs-lookup"><span data-stu-id="74a88-539">Tables</span></span>  
  
-   <span data-ttu-id="74a88-540">資料行</span><span class="sxs-lookup"><span data-stu-id="74a88-540">Columns</span></span>  
  
-   <span data-ttu-id="74a88-541">程序</span><span class="sxs-lookup"><span data-stu-id="74a88-541">Procedures</span></span>  
  
-   <span data-ttu-id="74a88-542">檢視</span><span class="sxs-lookup"><span data-stu-id="74a88-542">Views</span></span>  
  
-   <span data-ttu-id="74a88-543">Indexes</span><span class="sxs-lookup"><span data-stu-id="74a88-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="74a88-544">資料表</span><span class="sxs-lookup"><span data-stu-id="74a88-544">Tables</span></span>  
  
|<span data-ttu-id="74a88-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="74a88-545">ColumnName</span></span>|<span data-ttu-id="74a88-546">DataType</span><span class="sxs-lookup"><span data-stu-id="74a88-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="74a88-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="74a88-547">TABLE_CATALOG</span></span>|<span data-ttu-id="74a88-548">String</span><span class="sxs-lookup"><span data-stu-id="74a88-548">String</span></span>|  
|<span data-ttu-id="74a88-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="74a88-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="74a88-550">String</span><span class="sxs-lookup"><span data-stu-id="74a88-550">String</span></span>|  
|<span data-ttu-id="74a88-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-551">TABLE_NAME</span></span>|<span data-ttu-id="74a88-552">String</span><span class="sxs-lookup"><span data-stu-id="74a88-552">String</span></span>|  
|<span data-ttu-id="74a88-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="74a88-553">TABLE_TYPE</span></span>|<span data-ttu-id="74a88-554">String</span><span class="sxs-lookup"><span data-stu-id="74a88-554">String</span></span>|  
|<span data-ttu-id="74a88-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="74a88-555">TABLE_GUID</span></span>|<span data-ttu-id="74a88-556">Guid</span><span class="sxs-lookup"><span data-stu-id="74a88-556">Guid</span></span>|  
|<span data-ttu-id="74a88-557">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="74a88-557">DESCRIPTION</span></span>|<span data-ttu-id="74a88-558">String</span><span class="sxs-lookup"><span data-stu-id="74a88-558">String</span></span>|  
|<span data-ttu-id="74a88-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="74a88-559">TABLE_PROPID</span></span>|<span data-ttu-id="74a88-560">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-560">Int64</span></span>|  
|<span data-ttu-id="74a88-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="74a88-561">DATE_CREATED</span></span>|<span data-ttu-id="74a88-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="74a88-562">DateTime</span></span>|  
|<span data-ttu-id="74a88-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="74a88-563">DATE_MODIFIED</span></span>|<span data-ttu-id="74a88-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="74a88-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="74a88-565">資料行</span><span class="sxs-lookup"><span data-stu-id="74a88-565">Columns</span></span>  
  
|<span data-ttu-id="74a88-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="74a88-566">ColumnName</span></span>|<span data-ttu-id="74a88-567">DataType</span><span class="sxs-lookup"><span data-stu-id="74a88-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="74a88-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="74a88-568">TABLE_CATALOG</span></span>|<span data-ttu-id="74a88-569">String</span><span class="sxs-lookup"><span data-stu-id="74a88-569">String</span></span>|  
|<span data-ttu-id="74a88-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="74a88-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="74a88-571">String</span><span class="sxs-lookup"><span data-stu-id="74a88-571">String</span></span>|  
|<span data-ttu-id="74a88-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-572">TABLE_NAME</span></span>|<span data-ttu-id="74a88-573">String</span><span class="sxs-lookup"><span data-stu-id="74a88-573">String</span></span>|  
|<span data-ttu-id="74a88-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-574">COLUMN_NAME</span></span>|<span data-ttu-id="74a88-575">String</span><span class="sxs-lookup"><span data-stu-id="74a88-575">String</span></span>|  
|<span data-ttu-id="74a88-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="74a88-576">COLUMN_GUID</span></span>|<span data-ttu-id="74a88-577">Guid</span><span class="sxs-lookup"><span data-stu-id="74a88-577">Guid</span></span>|  
|<span data-ttu-id="74a88-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="74a88-578">COLUMN_PROPID</span></span>|<span data-ttu-id="74a88-579">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-579">Int64</span></span>|  
|<span data-ttu-id="74a88-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="74a88-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="74a88-581">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-581">Int64</span></span>|  
|<span data-ttu-id="74a88-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="74a88-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="74a88-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-583">Boolean</span></span>|  
|<span data-ttu-id="74a88-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="74a88-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="74a88-585">String</span><span class="sxs-lookup"><span data-stu-id="74a88-585">String</span></span>|  
|<span data-ttu-id="74a88-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="74a88-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="74a88-587">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-587">Int64</span></span>|  
|<span data-ttu-id="74a88-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="74a88-588">IS_NULLABLE</span></span>|<span data-ttu-id="74a88-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-589">Boolean</span></span>|  
|<span data-ttu-id="74a88-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="74a88-590">DATA_TYPE</span></span>|<span data-ttu-id="74a88-591">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-591">Int32</span></span>|  
|<span data-ttu-id="74a88-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="74a88-592">TYPE_GUID</span></span>|<span data-ttu-id="74a88-593">Guid</span><span class="sxs-lookup"><span data-stu-id="74a88-593">Guid</span></span>|  
|<span data-ttu-id="74a88-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="74a88-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="74a88-595">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-595">Int64</span></span>|  
|<span data-ttu-id="74a88-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="74a88-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="74a88-597">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-597">Int64</span></span>|  
|<span data-ttu-id="74a88-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="74a88-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="74a88-599">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-599">Int32</span></span>|  
|<span data-ttu-id="74a88-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="74a88-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="74a88-601">Int16</span><span class="sxs-lookup"><span data-stu-id="74a88-601">Int16</span></span>|  
|<span data-ttu-id="74a88-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="74a88-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="74a88-603">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-603">Int64</span></span>|  
|<span data-ttu-id="74a88-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="74a88-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="74a88-605">String</span><span class="sxs-lookup"><span data-stu-id="74a88-605">String</span></span>|  
|<span data-ttu-id="74a88-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="74a88-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="74a88-607">String</span><span class="sxs-lookup"><span data-stu-id="74a88-607">String</span></span>|  
|<span data-ttu-id="74a88-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="74a88-609">String</span><span class="sxs-lookup"><span data-stu-id="74a88-609">String</span></span>|  
|<span data-ttu-id="74a88-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="74a88-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="74a88-611">String</span><span class="sxs-lookup"><span data-stu-id="74a88-611">String</span></span>|  
|<span data-ttu-id="74a88-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="74a88-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="74a88-613">String</span><span class="sxs-lookup"><span data-stu-id="74a88-613">String</span></span>|  
|<span data-ttu-id="74a88-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-614">COLLATION_NAME</span></span>|<span data-ttu-id="74a88-615">String</span><span class="sxs-lookup"><span data-stu-id="74a88-615">String</span></span>|  
|<span data-ttu-id="74a88-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="74a88-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="74a88-617">String</span><span class="sxs-lookup"><span data-stu-id="74a88-617">String</span></span>|  
|<span data-ttu-id="74a88-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="74a88-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="74a88-619">String</span><span class="sxs-lookup"><span data-stu-id="74a88-619">String</span></span>|  
|<span data-ttu-id="74a88-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-620">DOMAIN_NAME</span></span>|<span data-ttu-id="74a88-621">String</span><span class="sxs-lookup"><span data-stu-id="74a88-621">String</span></span>|  
|<span data-ttu-id="74a88-622">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="74a88-622">DESCRIPTION</span></span>|<span data-ttu-id="74a88-623">String</span><span class="sxs-lookup"><span data-stu-id="74a88-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="74a88-624">程序</span><span class="sxs-lookup"><span data-stu-id="74a88-624">Procedures</span></span>  
  
|<span data-ttu-id="74a88-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="74a88-625">ColumnName</span></span>|<span data-ttu-id="74a88-626">DataType</span><span class="sxs-lookup"><span data-stu-id="74a88-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="74a88-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="74a88-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="74a88-628">String</span><span class="sxs-lookup"><span data-stu-id="74a88-628">String</span></span>|  
|<span data-ttu-id="74a88-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="74a88-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="74a88-630">String</span><span class="sxs-lookup"><span data-stu-id="74a88-630">String</span></span>|  
|<span data-ttu-id="74a88-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="74a88-632">String</span><span class="sxs-lookup"><span data-stu-id="74a88-632">String</span></span>|  
|<span data-ttu-id="74a88-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="74a88-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="74a88-634">Int16</span><span class="sxs-lookup"><span data-stu-id="74a88-634">Int16</span></span>|  
|<span data-ttu-id="74a88-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="74a88-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="74a88-636">String</span><span class="sxs-lookup"><span data-stu-id="74a88-636">String</span></span>|  
|<span data-ttu-id="74a88-637">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="74a88-637">DESCRIPTION</span></span>|<span data-ttu-id="74a88-638">String</span><span class="sxs-lookup"><span data-stu-id="74a88-638">String</span></span>|  
|<span data-ttu-id="74a88-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="74a88-639">DATE_CREATED</span></span>|<span data-ttu-id="74a88-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="74a88-640">DateTime</span></span>|  
|<span data-ttu-id="74a88-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="74a88-641">DATE_MODIFIED</span></span>|<span data-ttu-id="74a88-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="74a88-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="74a88-643">檢視</span><span class="sxs-lookup"><span data-stu-id="74a88-643">Views</span></span>  
  
|<span data-ttu-id="74a88-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="74a88-644">ColumnName</span></span>|<span data-ttu-id="74a88-645">DataType</span><span class="sxs-lookup"><span data-stu-id="74a88-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="74a88-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="74a88-646">TABLE_CATALOG</span></span>|<span data-ttu-id="74a88-647">String</span><span class="sxs-lookup"><span data-stu-id="74a88-647">String</span></span>|  
|<span data-ttu-id="74a88-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="74a88-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="74a88-649">String</span><span class="sxs-lookup"><span data-stu-id="74a88-649">String</span></span>|  
|<span data-ttu-id="74a88-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-650">TABLE_NAME</span></span>|<span data-ttu-id="74a88-651">String</span><span class="sxs-lookup"><span data-stu-id="74a88-651">String</span></span>|  
|<span data-ttu-id="74a88-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="74a88-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="74a88-653">String</span><span class="sxs-lookup"><span data-stu-id="74a88-653">String</span></span>|  
|<span data-ttu-id="74a88-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="74a88-654">CHECK_OPTION</span></span>|<span data-ttu-id="74a88-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-655">Boolean</span></span>|  
|<span data-ttu-id="74a88-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="74a88-656">IS_UPDATABLE</span></span>|<span data-ttu-id="74a88-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-657">Boolean</span></span>|  
|<span data-ttu-id="74a88-658">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="74a88-658">DESCRIPTION</span></span>|<span data-ttu-id="74a88-659">String</span><span class="sxs-lookup"><span data-stu-id="74a88-659">String</span></span>|  
|<span data-ttu-id="74a88-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="74a88-660">DATE_CREATED</span></span>|<span data-ttu-id="74a88-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="74a88-661">DateTime</span></span>|  
|<span data-ttu-id="74a88-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="74a88-662">DATE_MODIFIED</span></span>|<span data-ttu-id="74a88-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="74a88-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="74a88-664">Indexes</span><span class="sxs-lookup"><span data-stu-id="74a88-664">Indexes</span></span>  
  
|<span data-ttu-id="74a88-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="74a88-665">ColumnName</span></span>|<span data-ttu-id="74a88-666">DataType</span><span class="sxs-lookup"><span data-stu-id="74a88-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="74a88-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="74a88-667">TABLE_CATALOG</span></span>|<span data-ttu-id="74a88-668">String</span><span class="sxs-lookup"><span data-stu-id="74a88-668">String</span></span>|  
|<span data-ttu-id="74a88-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="74a88-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="74a88-670">String</span><span class="sxs-lookup"><span data-stu-id="74a88-670">String</span></span>|  
|<span data-ttu-id="74a88-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-671">TABLE_NAME</span></span>|<span data-ttu-id="74a88-672">String</span><span class="sxs-lookup"><span data-stu-id="74a88-672">String</span></span>|  
|<span data-ttu-id="74a88-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="74a88-673">INDEX_CATALOG</span></span>|<span data-ttu-id="74a88-674">String</span><span class="sxs-lookup"><span data-stu-id="74a88-674">String</span></span>|  
|<span data-ttu-id="74a88-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="74a88-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="74a88-676">String</span><span class="sxs-lookup"><span data-stu-id="74a88-676">String</span></span>|  
|<span data-ttu-id="74a88-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-677">INDEX_NAME</span></span>|<span data-ttu-id="74a88-678">String</span><span class="sxs-lookup"><span data-stu-id="74a88-678">String</span></span>|  
|<span data-ttu-id="74a88-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="74a88-679">PRIMARY_KEY</span></span>|<span data-ttu-id="74a88-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-680">Boolean</span></span>|  
|<span data-ttu-id="74a88-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="74a88-681">UNIQUE</span></span>|<span data-ttu-id="74a88-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-682">Boolean</span></span>|  
|<span data-ttu-id="74a88-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="74a88-683">CLUSTERED</span></span>|<span data-ttu-id="74a88-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-684">Boolean</span></span>|  
|<span data-ttu-id="74a88-685">TYPE</span><span class="sxs-lookup"><span data-stu-id="74a88-685">TYPE</span></span>|<span data-ttu-id="74a88-686">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-686">Int32</span></span>|  
|<span data-ttu-id="74a88-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="74a88-687">FILL_FACTOR</span></span>|<span data-ttu-id="74a88-688">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-688">Int32</span></span>|  
|<span data-ttu-id="74a88-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="74a88-689">INITIAL_SIZE</span></span>|<span data-ttu-id="74a88-690">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-690">Int32</span></span>|  
|<span data-ttu-id="74a88-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="74a88-691">NULLS</span></span>|<span data-ttu-id="74a88-692">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-692">Int32</span></span>|  
|<span data-ttu-id="74a88-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="74a88-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="74a88-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-694">Boolean</span></span>|  
|<span data-ttu-id="74a88-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="74a88-695">AUTO_UPDATE</span></span>|<span data-ttu-id="74a88-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-696">Boolean</span></span>|  
|<span data-ttu-id="74a88-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="74a88-697">NULL_COLLATION</span></span>|<span data-ttu-id="74a88-698">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-698">Int32</span></span>|  
|<span data-ttu-id="74a88-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="74a88-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="74a88-700">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-700">Int64</span></span>|  
|<span data-ttu-id="74a88-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="74a88-701">COLUMN_NAME</span></span>|<span data-ttu-id="74a88-702">String</span><span class="sxs-lookup"><span data-stu-id="74a88-702">String</span></span>|  
|<span data-ttu-id="74a88-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="74a88-703">COLUMN_GUID</span></span>|<span data-ttu-id="74a88-704">Guid</span><span class="sxs-lookup"><span data-stu-id="74a88-704">Guid</span></span>|  
|<span data-ttu-id="74a88-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="74a88-705">COLUMN_PROPID</span></span>|<span data-ttu-id="74a88-706">Int64</span><span class="sxs-lookup"><span data-stu-id="74a88-706">Int64</span></span>|  
|<span data-ttu-id="74a88-707">COLLATION</span><span class="sxs-lookup"><span data-stu-id="74a88-707">COLLATION</span></span>|<span data-ttu-id="74a88-708">Int16</span><span class="sxs-lookup"><span data-stu-id="74a88-708">Int16</span></span>|  
|<span data-ttu-id="74a88-709">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="74a88-709">CARDINALITY</span></span>|<span data-ttu-id="74a88-710">Decimal</span><span class="sxs-lookup"><span data-stu-id="74a88-710">Decimal</span></span>|  
|<span data-ttu-id="74a88-711">PAGES</span><span class="sxs-lookup"><span data-stu-id="74a88-711">PAGES</span></span>|<span data-ttu-id="74a88-712">Int32</span><span class="sxs-lookup"><span data-stu-id="74a88-712">Int32</span></span>|  
|<span data-ttu-id="74a88-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="74a88-713">FILTER_CONDITION</span></span>|<span data-ttu-id="74a88-714">String</span><span class="sxs-lookup"><span data-stu-id="74a88-714">String</span></span>|  
|<span data-ttu-id="74a88-715">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="74a88-715">INTEGRATED</span></span>|<span data-ttu-id="74a88-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="74a88-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="74a88-717">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74a88-717">See also</span></span>
- [<span data-ttu-id="74a88-718">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="74a88-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
