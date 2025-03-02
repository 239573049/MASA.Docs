# 产品介绍

## MASA Auth是什么产品？

MASA Auth是MASA Stack中最核心的功能之一，它统一负责了所有产品的权限、菜单、用户等。它包含了单点登录、用户管理、RBAC3、第三方平台接入、Ldap等企业级功能。除了可以用在企业内部管理系统，它还可以帮助管理C端用户。

## 用户群体

IT运维、人事HR、项目管理员、后端开发。

## 产品定位

在围绕以用户为对象的项目中，认证授权，单点登录以及配置用户信息是几乎所有互联网项目不可缺少的一部分内容。MASA Auth以市面上最常用的功能作为基础能力，提供一整套完整的用户登录解决方案。其中包含了所有登录的界面配置以及用户来源等。

## 产品目标

通过对用户的来源、权限配置、团队归属、用户个人信息绑定等功能实现快速搭建用户登录的相关体系。实现业务项目的快速落地。

## 需求背景

98%的互联网产品都是以用户的各种需求为主导，包含用户的生活需求、用户的操作需求、用户行为需求等。可以简单的理解为绝大多数场景下系统都需要有用户。该需求背景具有广泛性和普遍性。

## 产品结构如图

![MASA Auth功能结构图](https://cdn.masastack.com/stack/doc/auth/introduce/functional-structure.svg)

![MASA Auth功能结构详细图](https://cdn.masastack.com/stack/doc/auth/introduce/functional-structure-detail.svg)

## MASA Auth有哪些功能特性与优势

### 用户管理

支持多类用户，包括终端用户、第三方用户（QQ/微信/Github/域用户等）、员工（内部员工/外部员工）。可对用户基础信息、详细信息、员工信息（包含所在团队）、权限、身份等进行调整。提供全局产品的用户个人中心的管理页面。 

![用户管理图](https://cdn.masastack.com/stack/doc/auth/introduce/user-functional.svg)

### 用户管理分权

<div class="m-sheet m-sheet--outlined rounded theme--light mb-2">
    <div class="m-data-table m-data-table--fixed-height theme--light">
        <div class="m-data-table__wrapper">
            <table>
                <thead>
                    <tr>
 	                    <th style="border-right: thin solid rgba(0,0,0,.12);">应用场景</th>
 	                    <th>描述</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
 	                    <td rowspan="6" style="border-right: thin solid rgba(0,0,0,.12); vertical-align: text-top; padding-top: 13px;">用户管理与分权</td>
 	                    <td>-提供员工/用户独立账号，并独立分配权限做到责权一致</td>
                    </tr>
                    <tr>
 	                    <td>-可以将管理权限分权给不同类型用户进行登录和操作</td>
                    </tr>
                    <tr>
 	                    <td>-用户/员工需要独立获取授权，授权以后可以操作资源。并有记录，符合审计标准。</td>
                    </tr>
                    <tr>
 	                    <td>-可以随时冻结或取消用户/员工账号所有的权限。</td>
                    </tr>
                    <tr>
 	                    <td>-用户/员工授权有时间限制，关联授权令牌相关设置。</td>
                    </tr>
                    <tr>
 	                    <td>-用户/员工可以通过多渠道授权注册与登录。</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
</div>

### 什么是RBAC3模型

RBAC 认为权限授权实际上是 Who What How 的问题, 即 “Who 对 What 进行 How 的操作”。是"主体"对"客体"的操作, 其中Who是权限的拥有者（User, Role）–主体, What 是资源或对象（Resource，Class）。

![RBAC用户授权图](https://cdn.masastack.com/stack/doc/auth/introduce/rbac-user-auth.png)

RBAC1 模型主要增加了角色继承的概念，很多业务场景中，角色存在上下级关系。比如银行业务中省行的行长和地市分行的行长之间的关系、大型集团公司业务中大区经理和片区经理之间的关系；

RBAC2 模型主要增加了责任分离关系，面向授权访问添加了诸多约束，这也是为了满足业务的需要。比如在企业内部，出纳和会计是两个不同的角色，这两个角色如果由一个人来担任，则可能会出现资金流失而无人知晓的情况，所以在 RBAC 模型实现时，通过授权约束，限制同一个人被授予出纳和会计这两个角色，以规避风险；

RBAC3 模型是 RBAC1 和 RBAC2 的组合，既添加了角色继承，又有访问控制约束，以满足更加复杂的业务需求。

RBAC3技术实现

在调用 API 的可视化组件中，最常见的是前端 Web 页面。通常来说，一个前端 Web 页面包含以下元素。

* 模块：是指多个业务功能相近的功能组合，比如用户管理模块中有用户注册、用户信息修改、用户注销、用户锁定等。
* 菜单：通常对应某个具体的业务功能页面，有上级菜单和子菜单的区别。
* 按钮：是指页面上的操作按钮，比如新增按钮、修改按钮、删除按钮等。
* 链接：页面主体部分显示的除按钮外需要进行访问控制的超链接。
* 数据：页面显示的业务数据、资源、文件等。

### 权限策略

* 在MASA Stack产品中，权限主要有Auth进行管理。权限分为前端权限、API权限，目前权限类型仅提供菜单权限。
* 权限可以授权给对应的角色，并设置独立的权限名称。支持中/英文两种名称。
* API权限不能直接分配给指定角色与用户，需要挂靠在前端权限下才可以随着前端权限进行使用。
* 权限层级优先级为：个人＞角色＞继承角色＞项目团队 避免权限互斥造成的异常。

### SSO单点登录

单点登录(SingleSignOn，SSO)，就是通过用户的一次性鉴别登录。当用户在身份认证服务器上登录一次以后，即可获得访问单点登录系统中其他关联系统和应用软件的权限，同时这种实现是不需要管理员对用户的登录状态或其他信息进行修改的，这意味着在多个应用系统中，用户只需一次登录就可以访问所有相互信任的应用系统。这种方式减少了由登录产生的时间消耗，辅助了用户管理，是比较流行的。	

* 认证用户/员工，识别其对应来源与身份
* 授权给认证用户/员工可以登录的平台以及操作权限
* 安全防止伪造身份验证

在MASA Stack中通过Auth认证授权的用户可以拥有整个MASA Stack产品相关操作权限。可以登录其相关的所有平台。

### 组织架构

提供无限级组织架构管理工具，适用与企业级所需要的设置部门编排人员与用户。根节点是唯一不可删除。

部门管理增加了快速复制部门的功能，可以快速新增或者调整部门中的相关人员管理。

说明：MASA Auth 组织架构不涉及任何角色权限相关的挂靠，虽然有层级区分单并没有影响实际权限的层级，具体如何适用可以灵活变通适用来满足需求场景。

### 用户登录与用户授权

用户登录Auth以及MASA Stack其他项目平台所登录的界面均可通过Auth来进行配置，可以在Auth进行统一管理。

用户登录MASA Stack产品的授权统一由Auth进行管理。可以对授权页面进行调整。包括调整用户须知等协议。

### 项目团队

项目团队是在人员组织以及项目之外再增加的一个圈层，可以用于管理临时的项目。适用场景比较广发，在不改变人员原有的组织架构，角色部门权限外再增加的项目团队组。项目团队设置有2个固定角色。

-项目团队管理员

-项目团队成员

项目团队成员的权限≤项目管理员 权限层级优先级相对最低。

项目团队管理员/项目团队成员设置权限时可以直接选择角色进行配权。

### 第三方支持

目前已经支持企业级域账号登录，可以配置域账号。

已经支持手机号码登录。

其他第三方可以通过Oauth增加客户端来进行配置

### 使用场景

MASA Auth属于一款综合性的用户管理产品，提供了目前市面上大部分常规产品该有的功能，并且进行了一定的组合可以提供更全适合更多场景使用的可能。 例如我们在公司企业中会有很多短期和应急性的变动，成立一个临时的项目组来完成某件事情或某些指标。 那么在不变动原有岗位与权限的基础上需要开通关于临时项目组的权限内容，这里我们就可以通过项目管理来实现这一需求，作为MASA Stack 1.0的核心产品，Auth同时提供单点登录来并联整个系统矩阵中的其他产品。 MASA Auth与MASA DCC、MASA PM可以作为最初底层三件套产品一站式解决项目初期时的问题。
