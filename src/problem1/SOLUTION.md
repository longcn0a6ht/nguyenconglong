grep "TSLA" ./transaction-log.txt | grep '"side": "sell"' | awk '{print $2}' | tr -d '",' | while read -r ORDER_ID; do echo "https://example.com/api/:$ORDER_ID" >> ./output.txt;  done
