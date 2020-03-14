<template>
    <div>
        <div id="slogan">
            <div class="text-center">
                <h1>NameGator</h1>
                <br />
                <h6 class="text-secondary">Um gerador de nomes usando Node.js, Vue e GraphQL</h6>
            </div>
        </div>
		
        <div id="main">
			<router-view></router-view>
        </div>
    </div>
</template>

<script>
import "font-awesome/css/font-awesome.css";
import "bootstrap/dist/css/bootstrap.css";
import DomainList from "./components/DomainList";

export default {
	name: "App",
	components:{
		DomainList
	}
};
</script>

<style>
#slogan {
    margin: 30px 0;
}

#main {
    background-color: #f1f1f1;
    padding: 30px 0;
}
</style>
