<template>
    <div class="container">
        <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
        <app-new-quote @quoteAdded="newQuote($event)"></app-new-quote>
        <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote($event)"></app-quote-grid>
        <div class="row">
            <div class="col-sm-12 text-center">
                <div class="alert alert-info">
                    Info: Click on a quote to delete it!
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import QuoteGrid from './components/QuoteGrid';
    import NewQuote from './components/NewQuote';
    import Header from './components/Header';
    export default {
       data: function(){
           return {
               quotes: [
                   'Just a quote to see somethings'
               ],
               maxQuotes: 10
           }
       },
       methods:{
           newQuote(quote){
               if(this.quotes.length >= this.maxQuotes){
                   return alert('please delete quote first!');
               } 
               this.quotes.push(quote);
           },
           deleteQuote(index){
               this.quotes.splice(index,1);
           }
       },
       components: {
           appQuoteGrid: QuoteGrid,
           appNewQuote: NewQuote,
           appHeader: Header
       } 
    }
</script>

<style>
</style>
