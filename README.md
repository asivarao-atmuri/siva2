from flask import flask, request
from google.cloud import storage
import os
app = flask(__name__)
@app.route('/process-file',methods=['post'])
def process_file():
        bucket_name='siva11'
        file_name = 'code-talk-fe'
        storage_client = storage.Client()
        bucket = storage_client.get_bucket(bucket_name)
        blob = bucket.blob(file_name)
        content = blob.download_as_text()
        return 'File processed successfully!',200
if __name__ =='__main__':
        app.run(host='0.0.0.0', port=8080)
