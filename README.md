<h3><strong>Установка Istio</strong></h3>
<p><strong>1.</strong> Установить istioctl:&nbsp; <em>sudo mv istio-1.5.1/bin/istioctl /usr/local/bin/</em></p>
<p><strong>2</strong>. Установить Istio на кластер:</p>
<p><em>istioctl manifest apply --set values.gateways.enabled=true --set values.gateways.istio-ingressgateway.enabled=true --set values.gateways.istio-ingressgateway.sds.enabled=true --set values.grafana.enabled=true --set values.kiali.enabled=true --set values.prometheus.enabled=true --set values.tracing.enabled=true</em></p>
<p><strong>3.&nbsp;</strong>Открыть доступ к компонентам мониторинга Istio:</p>
<p>Применить все yaml файлы из директории&nbsp;metrics/expose_istio_metrics, далее доступ по портам ниже</p>
<p>Kiali: http://&lt;IP ADDRESS OF CLUSTER INGRESS&gt;:15029/<br />Prometheus: http://&lt;IP ADDRESS OF CLUSTER INGRESS&gt;:15030/<br />Grafana: http://&lt;IP ADDRESS OF CLUSTER INGRESS&gt;:15031/<br />Tracing: http://&lt;IP ADDRESS OF CLUSTER INGRESS&gt;:15032/</p>
<hr />
<h3><strong>&nbsp;Установка компонентов мониторинга кластера</strong></h3>
<p><strong>1. </strong>Создать неймспейс monitoring:&nbsp;</p>
<p><em>kubectl create ns monitoring</em></p>
<p><strong>2.&nbsp;</strong>Prometeus:&nbsp;</p>
<p>Применить все yaml файлы из директории&nbsp;/metrics/prometeus, с приставкой к комманде -n monitoring, далее доступ к интерфейсу по пути:</p>
<p>http://&lt;IP ADDRESS OF CLUSTER INGRESS&gt;/prometeus</p>
<p><strong>3.&nbsp;</strong>Alertmanager:&nbsp;</p>
<p>Применить все yaml файлы из директории&nbsp;/metrics/alertmanager,с приставкой к комманде -n monitoring, далее доступ к интерфейсу по пути:</p>
<p>http://&lt;IP ADDRESS OF CLUSTER INGRESS&gt;/alertmanager</p>
<p><strong>4.&nbsp;</strong>Grafana:&nbsp;</p>
<p>Применить все yaml файлы из директории&nbsp;/metrics/grafana,&nbsp;с приставкой к комманде -n monitoring, далее доступ к интерфейсу по пути:</p>
<p>http://&lt;IP ADDRESS OF CLUSTER INGRESS&gt;/grafana</p>
<hr />
<h3><strong>Установка Bookinfo приложения&nbsp;</strong></h3>
<p><strong>1. </strong>Создать неймспейс bookinfo:&nbsp;</p>
<p><em>kubectl create ns bookinfo</em></p>
<p><strong><em>2.&nbsp;</em></strong>Применить все yaml файлы из директории /bookinfo, с приставкой к комманде -n bookinfo, далее доступ к приложению по пути:</p>
<p>http://&lt;IP ADDRESS OF CLUSTER INGRESS&gt;/productpage</p>
<p><strong>3.&nbsp;</strong>Метрики приложения доступны по адресу:</p>
<p>http://&lt;IP ADDRESS OF CLUSTER INGRESS&gt;/metrics</p>
