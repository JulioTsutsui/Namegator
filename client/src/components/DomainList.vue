<template>
    <div>
        <div id="main">
            <div class="container">
                <div class="row">
                    <div class="col-md">
						<AppItemList title="Prefixo" type="prefix" v-bind:items="items.prefix" v-on:addItem="addItem" v-on:deleteItem="deleteItem"></AppItemList>
                        
                    </div>
                    <div class="col-md">
						<AppItemList title="Sufixos" type="sufix" v-bind:items="items.sufix" v-on:addItem="addItem" v-on:deleteItem="deleteItem"></AppItemList>
                    </div>
                </div>
                <br />
                <h5>
                    Domínios
                    <span class="badge badge-info">{{ domains.length }}</span>
                </h5>
                <div class="card">
                    <div class="card-body">
                        <ul class="list-group">
                            <li class="list-group-item" v-for="domain in domains" v-bind:key="domain.name">
								<div class="row">
									<div class="col-md-6">
										{{domain.name}}
									</div>
									<div class="col-md-3">
										<span class="badge badge-info">{{(domain.available)?"Disponível":"Não disponível"}}</span>
									</div>
									<div class="col-md-3 text-right">
										<a v-bind:href="domain.checkout" class="btn btn-info" target="_blank">
											<span class="fa fa-shopping-cart"></span>
										</a>
										&nbsp;
										<button class="btn btn-info" @click="openDomain(domain)">
											<span class="fa fa-search"></span>
										</button>
									</div>
								</div>
							</li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import { mapState,mapActions } from "vuex";
import "font-awesome/css/font-awesome.css";
import "bootstrap/dist/css/bootstrap.css";
import AppItemList from "./AppItemList";

export default {
	name: "App",
	components:{
		AppItemList
	},
	data: function(){
		return {};
	},
	methods: {
		...mapActions(["addItem","deleteItem","getItems", "generateDomains"]),
		openDomain(domain){
			this.$router.push({
				path:`/domains/${domain.name}`
			});
		}
	},
	computed:{
		...mapState(["items","domains"])
	}
};
</script>

<style>

</style>
