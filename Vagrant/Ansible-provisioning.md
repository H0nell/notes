## Установка Vagrant для тестирования ролей Ansible
1. [Устанавливаем Vagrant](https://www.vagrantup.com/downloads)
2. Устанавливаем провайдера. В нашем случае virtualbox.
На MacOS:
```
brew install virtualbox
```
3. * При установке на MacOS нужно разрешить устанавливать дополнительные разрешения в Security & Privacy [скрин](https://i.stack.imgur.com/G82JQ.png)
4. Создаем базовый Vagrantfile, в котором указываем playbook для проверки и базовый image(box) системы, на котором он будет проверяться
```
Vagrant.configure("2") do |config|

  #
  # Run Ansible from the Vagrant Host
  #
  config.vm.box = "hashicorp/bionic64"
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
  end

end
```
[подробнее](https://www.vagrantup.com/docs/vagrantfile) о Vagrantfile
5. Поднимаем окружение с помощью
```
vagrant up
```
6. Подключаемся к виртуальной машине с помощью
```
vagrant ssh
```
