#/bin/bash------------------- Regex List [ you may add your own here] ---------------------------
ip="\b((25[0-5]|2[0-4][0-9]|[1][0-9][0-9]|[0-9][0-9]|[0-9])\.){3}(25[0-5]|2[0-4][0-9]|[1][0-9][0-9]|[0-9][0-9]|[0-9])\b"
email="\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,6}\b"
phone="(\b([0-9]{3}(\s|-)?[0-9]{3}(\s|-)?)|(\B\([0-9]{3}\)[0-9]{3}(\s|-)?))[0-9]{4}\b"
url="(https?:\/\/(?:www\.|(?!www))[a-zA-Z0-9][a-zA-Z0-9-]+[a-zA-Z0-9]\.[^\s]{2,}|www\.[a-zA-Z0-9][a-zA-Z0-9-]+[a-zA-Z0-9]\.[^\s]{2,}|https?:\/\/(?:www\.|(?!www))[a-zA-Z0-9]+\.[^\s]{2,}|www\.[a-zA-Z0-9]+\.[^\s]{2,})"
host="^(([a-zA-Z0-9]{1}[a-zA-Z0-9-]*[a-zA-Z0-9]{1}|[a-zA-Z0-9])\.)+(?<!www\.)[a-zA-Z]{1}[a-zA-Z0-9-]{0,22}[a-zA-Z0-9]{1}$" #this can be either a domain or a subdomain

found=false



arg_position=1
for arg in $(echo -n $3);
do
	[[ "$arg" == "$1" ]] &&  found=true && let "arg_position=arg_position +1" && break
 	let "arg_position=arg_position +1"
done




if  ! $found 
then
	exit 1

else


	value=`echo $3 | awk -v "col=${arg_position}" '{print $col}'`
	quote=`echo -n "$value" | grep -Eo "^('|\")"`

	if [ ! -z $quote ]
	then

		value=`echo $3 | grep -Po "$value.+?($quote|$)"`

	fi

	if [ ! $2  == "any" ]

	then

		echo $value | grep -Po ${!2} > /dev/null && echo $value | sed "s/^\([\"']\)\(.*\)\1\$/\2/g" || exit 2
	else
		echo $value
	fi

fi
