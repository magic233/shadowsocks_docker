#!/bin/bash
#version=0.1(test)
function menu(){
	clear
	echo "----------------------------------"
	echo "1.Install shadowsocks"
	echo "2.Start shadowsocks"
	echo "3.Stop shadowsocks"
	echo "4.View port&password"
	echo "5.Stop&Remove shadowsocks images"
	echo "6.exit"
	echo "----------------------------------"
	read -p "Please enter number[1-6]:" num1
case $num1 in
		1)
		echo docker pull teddysun/shadowsocks-libev
		if [ ! -d "/etc/shadowsocks-libev/" ];then
		mkdir /etc/shadowsocks-libev/
		echo "mkdir /etc/shadowsocks-libev successfully..."
		fi
		read -p "Please enter shadowsocks port number:" port_num
		read -p "Please enter shadowsocks password:" password
		echo "{\
    server":"0.0.0.0",\
    server_port":$port_num,\
    password":"password0",\
    timeout":300,\
    method":"aes-256-gcm",\
    fast_open":true,\
    nameserver":"8.8.8.8",\
    mode":"tcp_and_udp" \
    }"> /etc/shadowsocks-libev/config.json
		echo "$port_num" > /etc/shadowsocks-libev/port_tmp
		echo "Configuration file written successfully..."
		docker run -d -p $port_num:$port_num -p $port_num:$port_num/udp --name ss-libev --restart=always -v /etc/shadowsocks-libev:/etc/shadowsocks-libev teddysun/shadowsocks-libev
		echo "Start shadowsocks->port:$port_num successfully..."
		echo "port:$port_num \
		method:aes-256-gcm \
		password:$password">/etc/shadowsocks-libev/config_tmp
		clear
		echo "---------successfully---------"
		echo "port:$port_num"
		echo "password:$password"
		echo "method:aes-256-gcm"
		echo "Please enjoy it"
		;;
		2)
		docker ps -a|grep shadowsocks-libev >/etc/shadowsocks-libev/tmp
		start_id=$(head -c 12 /etc/shadowsocks-libev/port_tmp)
		docker start $start_id
		echo "Start shadowsocks->$start_id successfully..."
		menu
		;;
		3)
		docker ps |grep shadowsocks-libev >/etc/shadowsocks-libev/tmp
		stop_id=$(head -c 12 /etc/shadowsocks-libev/tmp)
		docker stop $stop_id
		echo "Stop shadowsocks->$stop_id successfully..."
		menu
		;;
		4)
		cat /etc/shadowsocks-libev/config_tmp
		menu
		;;
		5)
		docker ps |grep shadowsocks-libev >/etc/shadowsocks-libev/tmp
		stop_id=$(head -c 12 /etc/shadowsocks-libev/tmp)
		docker stop $stop_id
		echo "Stop shadowsocks->$stop_id successfully..."
		docker rm $stop_id
		echo "Remove shadowsocks->$stop_id successfully..."
		docker docker rmi teddysun/shadowsocks-libev
		echo "Remove shadowsocks image successfully..."
		rm -rf /etc/shadowsocks
		echo "Remove shadowsocks config successfully..."
		clear 
		echo "================================="
		echo "=Remove shadowsocks successfully="
		echo "================================="
		menu
		;;
		6)
	exit 0
esac
}
menu
