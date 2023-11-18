from flask
import Flask, request, jsonify
from flask_restful
import Api, Resource
from elasticsearch
import Elasticsearch

app = Flask(__name__)
api = Api(app)
es = Elasticsearch()

class LogIngestor(Resource):
    def post(self):
        data = request.get_json()
        es.index(index='logs', body=data)
        return jsonify({"message": "Log ingested successfully"}), 201

api.add_resource(LogIngestor, '/ingest')

if __name__ == '__main__':
    app.run(port=3000)

from flask 
import Flask, request, render_template, jsonify
from flask_restful 
import Api, Resource
from elasticsearch 
import Elasticsearch

app = Flask(__name__)
api = Api(app)
es = Elasticsearch()

class LogSearch(Resource):
    def get(self):
        query = request.args.get('query', '')
        filters = {
            "level": request.args.get('level', ''),
            "message": request.args.get('message', ''),
            "resourceId": request.args.get('resourceId', ''),
            "timestamp": request.args.get('timestamp', ''),
            "traceId": request.args.get('traceId', ''),
            "spanId": request.args.get('spanId', ''),
            "commit": request.args.get('commit', ''),
            "metadata.parentResourceId": request.args.get('parentResourceId', '')
        }

        must_queries = [{"match": {key: value}} for key, value in filters.items() if value]
       
        if query:
            must_queries.append({"query_string": {"query": query}})

        body = {"query": {"bool": {"must": must_queries}}}
       
        result = es.search(index='logs', body=body)
        hits = result['hits']['hits']

        return jsonify({"results": hits})

api.add_resource(LogSearch, '/search')

if __name__ == '__main__':
    app.run(port=3001, debug=True)


curl "http://localhost:3001/search?level=error"
curl "http://localhost:3001/search?message=Failed+to+connect"
curl "http://localhost:3001/search?resourceId=server-1234"
curl "http://localhost:3001/search?timestamp=2023-09-10T00:00:00Z&timestamp=2023-09-15T23:59:59Z"   
