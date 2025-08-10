# Configuración del Laboratorio

## Configuración de red
- **Servidor Bastion**: `192.168.1.1`
- **Servidor CentOS01**: `192.168.1.3`
- **Servidor Ubuntu01**: `192.168.1.2`

## Instalaciones y preparación

# Probar conectividad con todos los hosts
ansible all -m ping

# Instalar Ansible Core
sudo dnf install ansible-core -y    

# Pasar claves SSH desde Bastion a los otros servidores
ssh-copy-id usuario@192.168.1.3
ssh-copy-id usuario@192.168.1.2

# Instalar colecciones necesarias de Ansible
ansible-galaxy collection install ansible.posix
ansible-galaxy collection install community.general

# Ejecutar con privilegios elevados (-K)
ansible-playbook playbooks/nfs_setup.yml -K
ansible-playbook playbooks/hardening.yml -K
