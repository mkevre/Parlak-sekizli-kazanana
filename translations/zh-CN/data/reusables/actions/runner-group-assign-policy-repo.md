1. Assign a policy for repository access.

    您可以将运行器组配置为可供特定的存储库列表或组织中的所有存储库访问。{% ifversion ghec or ghes %} 默认情况下，只有私有存储库可以访问运行器组中的运行器，但您可以覆盖此操作。 如果配置企业共享的组织的运行组，则不能覆盖此设置。{% endif %}
